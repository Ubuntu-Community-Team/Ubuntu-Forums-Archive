---
title: "mythbuntu 10.10 no audio, no web"
date: 2010-10-21
forum: Mythbuntu
---

### Post by rusty0101 on 2010-10-21
I ran into three problems when upgrading from 9.10 to 10.10

1. slave system wouldn't update because it couldn't 'update' the database template
2. no sound after 10.10 update on master front end.
3. no access to mythweb across lan.

1. I 'fixed' the first one by doing an 'sudo apt-get remove mythtv-backend' on the slave system before performing the upgrade to the os, then after I had it up and running with 10.10 I re-installed the mythtv-backend and it is running just fine.

2. This was more complicated. I've been a bit unhappy with aspects of this system for some time and hopefully what I have now is a more permanent fix. In /etc/modprobe.d/alsa-base.conf there are several sound card drivers listed. Most have 'index=-2' at the end of the line. The card that I want the system to use is an external SB Live! device with a fiber spdif to my tuner. This was being detected and given an index of 1 even when no other audio card was installed or detected. After finding the line with the driver for snd-usb-audio (actually 2 lines, not sure which one mattered, so changed both) I changed it to read "options snd-usb-audio index=0" and after reboot I now get '0 snd_usb_audio' in /proc/asound/modules
Next since I had been trying to get alsa to point at card 1 (while the sb live usb interface was there) I had created a .asoundrc file that contained:
```

pcm.!default {
type hw
card 1
}
ctl.!default {
type hw
card 1
}

```
and I had to change the 'card 1' lines to 'card 0' so that alsa would use the correct interface.

Finally I had to point at the spdif interface on the sound card in "Utilities/Setup" > "Setup" >"General" on the Audio System page, the audio output device becomes "ALSA:spdif"

Since in the digital mode there really is no volume control option, I disabled the "Use internal volume controls" on the Audio Mixer page as well.

3. Probably the easiest. For some reason the .htaccess file, or link disapeared out of the /var/www/mythweb directory. Actually the link still existed, but it's target no longer did. It had been pointing at /etc/mythtv/mythweb-htaccess which no longer existed after the upgrades. I'm not sure if this was intentional in that it replaced an existing .htaccess file with a link to a non-existing file, or if it deleted and recreated the /etc/mythtv folder without the target file. Doesn't really matter which I guess. In any case I recreated the file with the following contents:
```

AuthName "MythTV"
AuthType Basic
AuthUserFile /etc/htpasswd.users
Require valid-user 

```
then ran 'sudo htpasswd -c /etc/htpasswd.users username' (replaced username with a username I use) and entered the password for that user's view of mythweb twice, and finally restarted apache.

I still have a couple of things to work out. Boxee doesn't seem to be very happy at the moment. Considering I am starting to use "Hulu +" for some shows that I don't have available to me otherwise, the fact that Boxee isn't working bothers me a bit. Though if I can get firefox to work, I may forgo the Boxee software. It's just I rather like the Boxee platform, and would like to make use of it. We'll see how things go.

---

