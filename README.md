# Fiddler Spotify Adblock
Blocks Spotify ads using Fiddler

Since Spotify changed how their ads are delivered, simply blocking a few domains at DNS level is no longer enough.
Ads will now load from spclient.wg.spotify.com, but if you block this domain e.g. with your HOSTS file, Spotify will no longer work correctly.

### So how do we block ads?

Luckily, Spotify made it fairly simple to see how their ad-API works.
We just have to block outgoing request to ```/ad-logic/``` and ```/ads/``` from the ```spclient.wg.spotify.com``` domain and let all the others pass.

And that's what we do.

## How to install 

First of all download and install Fiddler from [here.](https://www.telerik.com/fiddler)

Then, there are two ways to install this script.

1. Copy/Paste the script directly into Fiddler
* Open Fiddler
* Go to Rules->Costumize Rules (CTRL+R)
* Locate the function ```static function OnBeforeRequest(oSession: Session)```
* Paste the script from ```Spotify-Adblock-Rule.txt``` at the end of this function

2.
* Clone this repository
* Compile it
* Maybe you need to change your Reference Path and/or the copy Path according to [this](https://docs.telerik.com/fiddler/Extend-Fiddler/CreateExtension)
* Restart Fiddler

Also make sure that you enabled HTTPS-Decryption in Tools->Options->HTTPS->Decrypt HTTPS traffic, otherwise it won't work!

## Also

If you don't want to keep the Fiddler GUI open, install it as a service. [Here's](http://fiddler.wikidot.com/runasservice) how to do that.

By the way: This method is of course not restricted to Fiddler. You just need to somehow block ```/ad-logic/``` and ```/ads/``` from ```spclient.wg.spotify.com```.
There are probably many ways to do that.
