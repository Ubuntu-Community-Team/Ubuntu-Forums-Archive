---
title: "Seeking Suggestions for Upgrading Mythbuntu"
date: 2013-03-02
forum: Mythbuntu
---

### Post by kulinskit on 2013-03-02
I have Mythbuntu 10.04 64 bit running with Myth 0.24.2.  It runs very stably and I have added a number of other programs and add-ons since the initial installation.  Such as MiroBridge, XBMC, IRW customization for my jp1 remote, carefully permissioned mounts to store video on my NAS, a long, custom written firewall, firmware for my 4 TV Avermedia cable TV cards, etc.  

I understand the 10.04 support is ending soon, I'd like to upgrade rather than start fresh, import the myth database, and reconfigure the environment and a bunch of 3rd party software and tweaks again. (The changes were made over so long a period I can't remember all of the steps, I'm a Windows user who just gets by in Mythbuntu using google for help configuring.)

Can someone suggest the route most likely to succeed?  The choices, as I see them:
Use Update-Manager to update to 12.04
Use Myth-Control Center to update 0.24 to 0.25 to 0.26

Or would doing the steps in the opposite order, or using someone's command-line recipe be better?  I hesitate about reversing the order above because I understand Mythbuntu 12.04 does not support 0.24, and I need the myth database to be updated.

Apologies in advance if this question has already been asked in the forums, I sifted through posts under "Upgrade 12.04" + "10.04" but found nothing appropo.

---

### Post by AlecJ on 2013-03-03
Use clonezilla or simlar and take an image before you start..
My system was where you are now, move to 0.25 first as it works without help on 12.04, then use Update manager and upgrade to 12.04.2
I got to 0.26 too soon, many things stopped working, it getting better now.
Can't say for your 4 TV Avermedia cable TV cards? I use TBS dvb-s and have to reload the firmware after each kernal update.
But everything else updated fine, including the remote frontends.

---

### Post by kulinskit on 2013-03-03
Thanks very much for your suggestions--it would not have worked without the clonezilla image!  I did exactly the order you suggested, 0.25 first and then to 12.04, somehow I let Mythwelcome shut itself down in the middle of the upgrade to 12.04.  There was no recovering after that but having the image let me start over again.  It all seems to be working very well now, even the Avermedia cards (they are OTA not cable, I misspoke above).  

I'll stay with 0.25 for a while in light of your comments.  Mainly I wanted 12.04 for since support for 10.04 is about to end.

---

