---
title: "Audigy 4 is not producing sound"
date: 2005-12-29
forum: Multimedia &amp; Video
---

### Post by F for Fragging on 2005-12-29
I use an Audigy 4 OEM under Ubuntu 5.10, and it doesn't produce any sound. I'd appreciate it if anyone could help me. already did some searching but without result.

- When I open Volume Control from the GNOME panel, and go to File -> Change Device, it lists two devices: 

0: Audigy 2 Value [Unknown] [Alsa Mixer]
1: SigmaTel STAC9750,51 (OSS Mixer)

The Audigy 2 Value is the selected device. Device #1 is probably my onboard sound, I have it disabled in my BIOS.

I have a dual boot with Windows XP, under WXP everything works fine. In Ubuntu I've tried connecting headphones and my Logitech Z-5500 speakerset (which is connected analog with 3 connectors), both don't work. I could give more information on this, but I doubt that the problem lies there, more likely it has something to do with my soundcard's config.

I also tried unmuting and increasing the volume of things in alsamixer/GNOME's Volume Control. No effect however.

---

### Post by Daskinil on 2005-12-29
i today just got the audigy 4 and getting no sound, i've been searching internet for hours but no solution, a few people on sites say it worked fine for them, i've tried everything post above mentions but still no sound. please, does anyone know how to help

---

### Post by miker on 2005-12-31
I got it working by compiling the latest alsa release. Download the stable release of the driver, library and utilities from [http://www.alsa-project.org/]("http://www.alsa-project.org/").

You'll need some packages first; type at the terminal

$ sudo apt-get install build-essential g++-3.4 libncurses5-dev gettext linux-headers-`uname -r`

and then follow the excellent documentation here:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=CA0108&module=emu10k1]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=CA0108&module=emu10k1").
Do the same thing described in the "note to Debian users", removing /etc/modutils/alsa-base if it already exists. 

This isn't an ideal solution and you may need to repeat when the kernel and/or alsa is updated, but I don't know a more Debianny/Ubuntuish way of going about it and the latest alsa looks like it will be in the next Ubuntu release.

---

### Post by F for Fragging on 2005-12-31
Thank you for your reply miker.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=all&release=all)

According to this the latest ALSA release - 10.10 - is already in Dapper. I think I'll download the latest Dapper snapshot instead then, since it seems an easier method and because I have bad experiences with compiling from source.

---

### Post by F for Fragging on 2006-01-02
Well, I replaced "breezy" with "dapper" everywhere in my /etc/apt/sources.list and started up Synaptic and installed alsa base 1.0.10 from Dapper. Rebooted, tested, but sound still doesn't work.

But miker, why did you gave me an URL which gives me instructions for the Audigy 2 ZS Value? I did mention that Ubuntu detected it as an Audigy 2 ZS Value, but it actually is an Audigy 4 OEM.

---

### Post by miker on 2006-01-02
Yes, I have an Audigy 4 too but I read somewhere that the Audigy 2 ZS Value drivers work. Have you tried the post-compile configuration steps from that page (thinking about it I could have tried that before compilation)? Also the libesd-alsa0 package might be needed, the default sink output I'm using in System->Preferences->Multimedia is ESD, though ALSA seems to work too.

---

### Post by F for Fragging on 2006-01-03
Thanks for your help, but I think I'm tired of this, I give up. I don't feel like following a two page HOWTO and all these difficulties. I'll wait for when Dapper is finished, hope it will work then without trouble.

---

### Post by milek on 2006-01-06
I had exactly same problem with my Audigy 4. Try read this page [http://linux.iuplog.com/default.asp?item=94639]("http://linux.iuplog.com/default.asp?item=94639") . When i type "sudo alsactl store" , sound works.

---

### Post by b_cybe on 2006-01-16
Well I think I have found the solution to this problem! I myself newly bought a audigy 4 and everything worked fine in windows, but not in ubuntu. Therefore I decided to search a little around. After a while I found [this]("https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy?highlight=%28audigy%29").
I did mostly the same, only one ting different that I choose the module emu10k1 instead of ca0106. After I had done everything the volume controll shut down, but I got that back with adding it to the panel again! And best off all sounds work with audigy 4.

---

### Post by F for Fragging on 2006-01-16
I haven't checked this topic for some time, I've just found the solution to my problem myself, and I'll share it with you:

[http://alsa.opensrc.org/emu10k1](http://alsa.opensrc.org/emu10k1)

> 2005-11-08 No sound out of the Audigy 4

If you have an "Audigy 4" card and already have alsa configured, but you get no sound out of it, try the following (only for analog outputs):

# alsamixer 

    * use the right arrow key to get to the "IEC958 Optical Raw Switch" and make sure it is off (if not press m);
    * press the right arrow key a few more times to get to the "Audigy Analog/Digital Output Jack" switch and make sure it is on (if not press m)

    (any other combination of these two switches won't allow you to get sound from the analog outputs of the card) 

now, you should get sound out of it

If you want to make these changes persistent, do the following

# alsactl store <the id of your sound card>

if you have only one sound card the following is sufficient

# alsactl store 0

BTW: don't worry if your Audigy 4 get's detected as an Audigy 2 Value, it will work anyway :)

if this helps, I'm using Alsa 1.0.10

This was all I had to do to get it working. Thanks for your comments everybody.

---

### Post by beerorkid on 2006-02-04
[QUOTE=b_cybe]Well I think I have found the solution to this problem! I myself newly bought a audigy 4 and everything worked fine in windows, but not in ubuntu. Therefore I decided to search a little around. After a while I found [this]("https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy?highlight=%28audigy%29").
I did mostly the same, only one ting different that I choose the module emu10k1 instead of ca0106. After I had done everything the volume controll shut down, but I got that back with adding it to the panel again! And best off all sounds work with audigy 4.[/QUOTE]

Way to much time wasted until I did this.  Thanks so much.

I tried so many different things, probbably borked a bunch of settings and your post leading to [https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy?highlight=%28audigy%29](https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy?highlight=%28audigy%29) and I did use the emu10k1 fixed it right up.  I did have to reboot though.

This was my last hurdle on a very long course of crazy things happening to my  new futureshop PC which I have severely upgraded.  Now I get to sit back and enjoy.

Thanks once again.

---

