---
title: "How to LDS General Conference BYU TV"
date: 2008-10-05
forum: Multimedia Software
---

### Post by regor210 on 2008-10-05
For BYU TV
Try clicking on the link below
[http://www.byutv.org/streaming/byutv.asx](http://www.byutv.org/streaming/byutv.asx)

Wait a bit and if nothing comes up goto
Applications>Accessories>Terminal
Then cut and past the whole line below inside the Terminal window and hit Enter?

mplayer -playlist [http://www.byutv.org/streaming/byutv.asx](http://www.byutv.org/streaming/byutv.asx)

If you need to install Mplayer cut and past the line below and hit Enter?.

sudo aptitude update && sudo aptitude install mplayer

Then try the 1st line again to start BYU TV.
BYU TV recommends Mplayer but I recommend VLC
------------------------------------------------------------------------------
VLC is a much nicer player
Cut and past the line below inside the Terminal window and hit Enter to install vlc.

sudo aptitude update && sudo aptitude install vlc mozilla-plugin-vlc

Cut and past this line to start BYU TV

vlc [http://www.byutv.org/streaming/byutv.asx](http://www.byutv.org/streaming/byutv.asx)
---------------------------------------------------------------------------------------------
CONFERENCE
For live feed skip down.  For viewing old Conferences you may need to use this How to.
Use wine. Note we are not going to drink it. haha
Its not perfect but it works.
**Warning** this how to uses the newest version (unstable) of wine and may have issues.

Get Wine 1.1.5
For Ubuntu Hardy (8.04):
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
open Terminal and cut and past the line below one at a time and hit enter

sudo wget [http://wine.budgetdedicated.com/apt/...t.d/hardy.list](http://wine.budgetdedicated.com/apt/...t.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install wine

Get Firefox for Windows

Go here and download the Windows version of firefox

[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

If you have trouble unzipping try

sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller

I downloaded it to my desktop. Right click on Firefox Setup .exe icon and open it with wine to install it.
Open Firefox for windows. There should be an icon on your desktop.
Now go here and download Flash player for windows

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

I downloaded it to my desktop. Right click on it to inatall.

Shut down Firefox for windows and restart it.

Installing the Firefox "Move Media Player" Extension

Goto ?Video Streams - Watch Conference Online

[http://www.lds.org/broadcast/gc/0,5161,8176,00.html](http://www.lds.org/broadcast/gc/0,5161,8176,00.html)

click on your language

When the next screen comes up click install "Move Media Player" / allow by clking on the bar to the upper right

When the player opens you can hear but not see. Click on the full screen box. after it opens hit Esc. now you should be able to see and hear.

------------------------------------------------
Live CONFERENCE
This is only available with live feed but seems to work the best!
 
How to LDS General Conference BYU TV
For October 2008 General Conference goto

[http://www.lds.org/broadcast/gc/0,5161,8176,00.html](http://www.lds.org/broadcast/gc/0,5161,8176,00.html)

Scroll down to

Additional Video Streams

click on (Windows Media) and open with totem
----------------------------------------------------------------------
Good luck and good viewing.

---

