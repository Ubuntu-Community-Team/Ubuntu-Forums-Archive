---
title: "Troubleshooting Facebook-Flash-thingies..."
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by Silent Warrior on 2010-05-06
Oh, the frustrations of modern cyberlife! ):P
I want to start out by pointing out that I'm running Mint 9 RC x86_64, but given its Ubuntu-base, I would expect most of the involved packages are just about identical to what's in the Lucid repositories.
My problem is that, for a while now, Flash-games on Facebook (YouTube-videos seem fine in every way), Treasure Madness to be precise, hasn't been working right.
(To those who play that nasty, nasty time-thief, the minigames have gone bonkers - only Minilovka, Memory, and the bonus game seem to finish as they should.)

I bring this to YOU instead of Mint-forums for the simple reason that this worked just fine off the Lucid LiveCD (having installed Flash once in, that is). So, I want to debug the hell out of this. How?

What plug-ins/extensions are loaded on the version of Firefox on the LiveCD (should be the same - 3.6.3)? At present, I have the following:
[LIST]
[*]Adobe Reader 9.3
[*]DivX Browser Plug-in [Gecko Media Player 0.9.9.2]
[*]DivX Web Player [1.4.0.233]
[*]IcedTea NPR Web Browser Plug-in [6b18-1.8-0ubuntu1]
[*]iTunes Application Detector
[*]MozPlugger 1.13.3
[*]mplayer plug-in [Gecko Media Player 0.9.9.2]
[*]OpenOffice.org plug-in
[*]QuickTime Plug-in 7.6.4
[*]QuickTime Plug-in 7.6.6
[*]RealPlayer 9 [Gecko Media Player 0.9.9.2]
[*]Shockwave Flash [10.0 r45]
[*]Silverlight Plug-in [3.0.40818.0]
[*]Skype Buttons for Kopete
[*]Windows Media Player plug-in [Gecko Media Player 0.9.9.2]
[*]Windows Media Player plug-in [Totem 2.30.0]
[*]VLC Multimedia plugin [Totem 2.30.0]
[*]Xine Plugin [1.0.2]
[*]Firefox (is) - localisation
[*]Firefox (sv-SE) - localisation
[*]1-Click YouTube Video downloader [1.4]
[*]Adblock Plus [1.1.3]
[*]Boost for Facebook [9.9.2]
[*]Clean and Close [2.5.1]
[*]Dcurrency [0.4.0]
[*]DownThemAll! [1.1.9]
[*]DownThemAll! AntiContainer [0.7.3]
[*]FirefoxNotify [1.5.4]
[*]FlashGot [1.2.1.21]
[*]Greasemonkey [0.8.20100211.5]
[*]Mint Search Enhancer [1.0]
[*]NoScript [1.9.9.74]
[*]Novell Moonlight [2.2]
[*]Personas [1.5.3]
[*]Personas Rotator [0.4]
[*]PlasmaNotify [0.3.1]
[*]Stylish [1.0.8]
[*]Ubuntu Firefox Modifications [0.9rc2]
[*]xclear [1.3]
[/LIST]
(And a couple of themes.)
NoScript is set to allow the things needed for the minigames, only blocking some ad-things that appears unrelated at a glance.

I don't know if it's relevant, but I also have Wine (1.2) installed, and it seems to pull in some 32-bit dependencies. Could that be what bit me?

If this requires more in-depth troubleshooting, I'll take it to the Mint-forums, promise.

[Edit] H-hey! It works just fine with Opera!

---

