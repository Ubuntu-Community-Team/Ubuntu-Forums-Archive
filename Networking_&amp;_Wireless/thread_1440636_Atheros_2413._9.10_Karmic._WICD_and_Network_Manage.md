---
title: "Atheros 2413. 9.10 Karmic. WICD and Network Manager. No go. Fix?"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-03-27
I installed 9.10 Karmic 32 bit on a laptop here that has an Atheros 2413 card in it. I could see the network and tried to connect. After 30 seconds of attempting to connect, it simply says disconnected.

Thinking network manager was to blame, I installed WICD and rebooted. I tried to connect to my network, but it came back with unable to get IP address. Okay, fine. So I check my iBook and Ubuntu work laptop... both are connected fine...

I tried other drivers within the WICD preferences... wext, ndiswrapper, madwifi... nothing worked.

I power cycled the router thinking something might have been borked with my wireless... but it's fine.

No matter what I do, I can't get this laptop online. Help, or it'll have to remain on XP forever. :( 

Wireless card = Atheros 2413.
Ubuntu 9.10 32 bit.
Toshiba Satellite L25 Laptop.

---

### Post by theozzlives on 2010-03-27
I know for at least 3 versions SAMBA is borked. If you can't connect to the Internet, try wired to get the restricted drivers for your wireless card.

---

### Post by Roasted on 2010-03-27
I did try wired, but there are no "restricted" drivers that get picked up because my card is picked up AUTOMATICALLY. :( :(

---

### Post by Roasted on 2010-03-28
Okay, I'm very confused now. I installed the Linux Module Backports or whatever. It was recommended to me in the Ubuntu IRC. Nothing afterwards happened, however I wasn't entirely sure what I was supposed to do after.

On a hunch I removed WPA security from my network. Having no security whatsoever, this laptop connected to the wireless... I add WPA security back, and it does the same thing again where it won't connect.

What would cause this? How can I fix it?????

EDIT - Okay. I'm frustrated and I've tried several different things. I'm doing a fresh install just in case any solution may come about that wouldn't work due to the many guides I've tried.

There has to be an easy answer. A lot of people report this card working fine. So here I am, I have a fresh install of Ubuntu 9.10 32 bit and I'm going to do all of the updates. After that, I'm doing nothing to it. What can I do? I need advice on how to get this fricken card working. :(

---

### Post by alexfish on 2010-03-28
Hi
From early days I had a Atheros wifi It was always a problem the easiest solution is to bork cards or usb devices  that do not work out of the box  or rely on ndis wrappers etc,
check out devices which work out of the box with linux or specific to Ubuntu, **This will send the message to manufacturers and the marketeers**, whilst this may seem cruel on the end user, in reality it is often the best solution

for reading

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)
regards

alexfish

---

### Post by Roasted on 2010-03-28
That's what I do. I intentionally avoid hardware that isn't Linux compatible out of the box. I've already sent emails to certain hardware vendors saying BECAUSE OF YOU NOT SUPPORTING LINUX I have AVOIDED you...

But that doesn't help me here. Today. Right now. With an older laptop that I already had and I'm just trying to get wireless working.

Anybody...

---

### Post by alexfish on 2010-03-28
Hi

on the above link there are further links to 

** Ubuntu**

 Follow instructions in Ubuntu wiki at 
 
[LIST]
[*] [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto).
[*] [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[/LIST]

 hope these can be of  help

  	 	 	 	 	 	  There is an old thread here but not for 9.10
 

 [http://ubuntuforums.org/showthread.php?t=987137&page=3](http://ubuntuforums.org/showthread.php?t=987137&page=3)
 

 will post more as I find them

regards

alexfish

---

### Post by Roasted on 2010-03-28
I would really like to not use ndiswrapper, because I have heard about people using the 2413 and it working perfectly fine. That tells me there has to be a way to get this working. Not to mention, I tried ndiswrapper with the XP 32 bit driver for the 2413 Atheros card and I kept getting an error, something about unsupported hardware...

For the record, I fired up a Jaunty LiveCD and I could connect to my WPA secured wireless network. Currently the laptop has Jaunty on it and will probably remain so since it doesn't seem Karmic is the most friendly with wireless. I've read from several sources that Karmic had quite a few issues it presented in regards to wireless. But of course, you always hear negatives when a new version comes out :P but it makes you wonder when I hear it a lot from this version in particular and here I am having an issue...

---

### Post by alexfish on 2010-03-28
Network Manager 0.8 is the latest version available in Karmic as the previous version was not the final build for it

there is also a daily for 0.8 but  don't know if still active

Details here 

[http://www.asoftsite.org/s9y/](http://www.asoftsite.org/s9y/)

regards

alexfish

---

### Post by Roasted on 2010-03-28
For what it's worth, 8.04.4 and 9.04 both worked with WPA security on my network with this card. I used the LiveCD of 8.04.4 to try it out and 9.04 as well, however 9.04 is a native install as of now and I plan to use it since it works.

I tried to use the daily build of 10.04 to see if it was fixed, because I'd REALLY like to know if any wireless issues of this nature would exist so far in Lucid, however, the LiveCD continually freezes up on me and I cannot do a full test to see if 10.04 will connect to my network as of now.

EDIT - Finally got Lucid 10.04 to try it. Didn't work. This makes me doubt Lucid's "fixing" of several wireless issues Karmic brought to the table. :( Let's hope the final release is all right...

---

