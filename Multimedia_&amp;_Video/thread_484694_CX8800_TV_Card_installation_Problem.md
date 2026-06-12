---
title: "CX8800 TV Card installation Problem"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by LeighT on 2007-06-26
I have installed a Leadtek Winfast DVT1000t tv card.
According to Hardware Information and lspci, modprobe etc the card is reconised, as a CX23880/1/2/3 PCI Video and Audio Decoder.
The problem seems to be that the dev/dvb and its content directory isn't there.
ay ideas?:confused::confused

---

### Post by stinkypudding on 2007-06-26
I had a similar problem with the HD5500.   After the latest kernal update, my mythtv went kapoot.   I had to download from souce, and enable DVB.

Try this, after downloading source package:

./configure --enable-dvb

---

### Post by LeighT on 2007-06-27
Thanks for the info stinkypudding.  I have taken it out and replace it with a Tevion card using a SAA7131 chip set Still no luck.
Looks like I'll have to keep using the one in the lounge;)

---

### Post by grege on 2007-06-28
Under feisty you may need to manually load modules, there is an issue with the cx88 module not loading the correct modules for some cards. I had to do this for my Winfast DTV2000 H. Good news DVB-t and remote now work.

modprobe

 ir-common
 dvb-core
 cx88-dvb

may need
 cx8800 
or
 cx88xx

if all works, then install Kaffeine from the repos. You should then have a DVB option appear in kaffeine. Set your region and do a scan and you are away.

I am still trying to get a /dev/radio for my FM module without luck, but the TV works flawlessly.

---

### Post by grege on 2007-06-28
Sorry - forgot

Once you have worked out the modules add them to /etc/modules so they load automatically in the future.

---

