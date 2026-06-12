---
title: "Hauppage novat usb2 kubuntu"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by Eddtr1 on 2007-10-16
I need help urgently!!!! :-

Just installed kubuntu as a partition on a media centre and all is well - the next step is to install linux mce and be away however!!! I cant install my Hauppage usb2 nova t card. I found a website which explains what to do  but i have no idea what it is talking about - i installed kubuntu yesterday so pretty new i think it is the feisty fawn edition. Can anyone help - i need some basic instruction!

thanks

---

### Post by anthonyJC on 2007-10-16
if red light on the Nova is presently off get the file named dvb-usb-nova-t-usb2-02.fw using Google 

open Konsole and paste in :

[COLOR="YellowGreen"]cd Desktop ; sudo cp dvb-usb-nova-t-usb2-02.fw //lib/firmware[/COLOR]

Now NOVA-T is installed, but you need to restart your machine(in Fiesty - but not necessary in Gutsy Gibbon - u can hot plug NOVA)  - after a reboot light operates. However you can't use it until you set up a viewer - takes longer than a nice apt-get :-) . 

MythTV takes far longer to set-up   (I've done NOVA-T on MythTV approximately five times.) I had a look at the guide you linked to - it's very good from P.O.V. of setting up that remote to extended functionality; but the firmware information is out-dated.

---

### Post by Eddtr1 on 2007-10-16
> **anthonyJC said:**
> Get the file named dvb-usb-nova-t-usb2-02.fw using google

open Konsole and paste in :

cd Desktop
sudo cp dvb-usb-nova-t-usb2-02.fw //lib/firmware

Now NOVA-T is installed, but you need to restart your machine ( red light on the Nova is presently off) - after a reboot light operates. However you can't use it until you set up a viewer - takes longer than a nice apt-get :-) . Get a viewer:

sudo apt-get install kclear

MythTV takes far longer to set-up so I recommend Kclear to start with-  (I've done NOVA-T on MythTV approximately five times.) I can't really help setup MythTV/Klear if you are not in the UK( on terrestrial (freeview)); because that's all I have experience in. So tell me if your doing terrestial in UK? - specify your location in your user profile. I had a look at the guide you linked to - it's very good from P.O.V. of setting up that remote to extended functionality; but the firmware information is outdated.

Thanks for the reply- I will give this ago later - any further help you can give would be great - I am in the UK using digital terestrial in liverpool. When i set it up correctly (hopefully that is) will it all work in LinuxMCE when i install that as well

Thanks again!!

---

### Post by anthonyJC on 2007-10-16
I would assume so (since LinuxMCE uses MythTV.) LinuxMCE website says you don't need to set it up, but with MythTV I got it working by creating the configuration files myself.  It's best if you ignore the section in my post about configuring a viewer and instead install LinuxMCE. If LinuxMCE does what it claims (I haven't used it), it should be finished.

---

### Post by Eddtr1 on 2007-10-16
> **anthonyJC said:**
> I would assume so (since LinuxMCE uses MythTV.) LinuxMCE website says you don't need to set it up, but with MythTV I got it working by creating the configuration files myself.  It's best if you ignore the section in my post about configuring a viewer and instead install LinuxMCE. If LinuxMCE does what it claims (I haven't used it), it should be finished.

Thanks ill install it later and let ya know - fingers crossed!!!

---

### Post by Eddtr1 on 2007-10-16
> **anthonyJC said:**
> I would assume so (since LinuxMCE uses MythTV.) LinuxMCE website says you don't need to set it up, but with MythTV I got it working by creating the configuration files myself.  It's best if you ignore the section in my post about configuring a viewer and instead install LinuxMCE. If LinuxMCE does what it claims (I haven't used it), it should be finished.

ok tried linux and linuxmce wont install but thats another issue!!!!

i did what you said about the console and the viewer but nothing seems to have worked - how do i find out if the happuage usb2 nova t box is actually installed properly? the red light is on but it has always been on - in kaffine i get a dvb menu but and when i scan for channels ii get signal but no actual channels are found - o bugger i might be edging closer to mce 205 at this rate lol!!!! thaqnkgod for dual bootups!?

---

### Post by anthonyJC on 2007-10-16
Haven't used Kaffine. If the red light is on, it is installed. Use URL:[http://www.digitaluk.co.uk/](http://www.digitaluk.co.uk/) and type in your post-code to find your transmitter. Then past into Konsole:
[COLOR="YellowGreen"]
sudo apt-get install dvb-utils[/COLOR]

The transmitter names used by scan are: (Liverpool may just be uk-WinterHill )
uk-Angus          uk-Dover       uk-Oxford      uk-SuttonColdfield
uk-Bilsdale       uk-DoverB      uk-PontopPike  uk-TheWrekin
uk-BlackHill      uk-Durris      uk-Redruth     uk-TheWrekinB
uk-BluebellHill   uk-EmleyMoor   uk-Reigate     uk-Waltham
uk-Caradon        uk-Hannington  uk-Rowridge    uk-WhitehawkHill
uk-CaradonHill    uk-Heathfield  uk-SandyHeath  uk-WinterHill
uk-Craigkelly     uk-Llanddona   uk-Storeton
uk-CrystalPalace  uk-Mendip      uk-SudburyB

Use command scan with the transmitter  (in Konsole)

[COLOR="YellowGreen"]scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-YOURTRANSMITTER > channels.conf [/COLOR]

e.g. (in konsole)

[COLOR="YellowGreen"]scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > channels.conf[/COLOR]

This creates your channels.conf. Then use channels.conf file in what ever viewer. 

In my first post I said you needed to configure  MythTV. The steps given in this post are the major part of that configuration. This configuration cannot be done using MythTV. If you ever decide to use MythTV (in Konsole):

[COLOR="YellowGreen"]sudo cp channels.conf /home/mythtv[/COLOR]

---

