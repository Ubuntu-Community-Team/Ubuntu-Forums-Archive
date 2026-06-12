---
title: "Ultra-noob needs help installing S2-3200 drivers"
date: 2007-11-11
forum: Mythbuntu
---

### Post by saiorse44 on 2007-11-11
Helllo everybody. :)

I am a Windows user that is beginning to make the migration to Linux.

I wish to install the experimental drivers for my Technotrend budget S2-3200 card, I have tried but I usually end up with a screen full of errors. :(

Could somebody be so kind as to write me a short beginners guide on how to get this card up and running on a clean install of Mythbuntu 7.10.

The drivers are available from here: [http://jusst.de/hg/multiproto/]("http://jusst.de/hg/multiproto/")

I have tried going into the directory of the extracted files and typing make but to no avail.

Are there other things I need to be doing like V4L?

Many Thanks,
Rob

---

### Post by Gothem on 2007-12-14
Hi there, i got my skystar hd working a few weeks ago, which is basicaly an relabled technotrend 3200, so if you could paste the error messages you are getting maybe i can help you.
And one thing you should check is wether you have the kernel sources (or kernel headers) for the kernel you are running installed.
uname -r should give you the kernel version number, it should look something like 2.6.20-2

Edit: I should have taken a better look at the date of the post.... nevermind

---

### Post by saiorse44 on 2008-01-09
Hi, many thanks for your reply.
Sorry for not getting back sooner on this one.

I got over my error messages by installing the kernel headers as advised by a poster on the TechSpot forums.
[http://www.techspot.com/vb/topic92558.html]("http://www.techspot.com/vb/topic92558.html")

The problem I have now is that although the /dev/dvb folder has now appeared/ it contains another folder called adapter0 in this folder there are four files called:
demux0
dvr0
fontend0
net0
however all four files are empty.

MythTV backend setup also hangs whilst tring to add a new capture card.

Any ideas?
Rob

---

### Post by Skerit on 2008-05-14
I have succesfully compiled the modules and I'm able to modprobe them but ...

for some completely unknown reason the modules do nothing when I load them. I get no /dev/dvb

I followed these instructions to install the driver to the letter: [http://wilco.bercot.org/debian/s2-3200.html](http://wilco.bercot.org/debian/s2-3200.html)


Some console output:

lspci
04:01.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

dmesg | grep saa
[   37.931073] Audiowerk 2 sound card (saa7146 chipset) detected and managed
[   38.332543] saa7146: register extension 'budget_ci dvb'.

I should be getting a lot more from that dmesg message!

---

