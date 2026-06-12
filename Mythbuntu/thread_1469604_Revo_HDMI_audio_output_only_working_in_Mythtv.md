---
title: "Revo HDMI audio output only working in Mythtv"
date: 2010-05-02
forum: Mythbuntu
---

### Post by stormb on 2010-05-02
Dear all,

Hopefully you can advise me on how to sort out my issue. I've got an Acer Aspire Revo running Mythbuntu 9.10 with the 0.22+fixes auto builds repository. It's connected to my TV via the HDMI input. In Myth I've manually selected the HDMI output and everything works fine for audio in it (I use DVB-T if it matters).

I'm having trouble with my non-Myth applications though. Specifically Adobe flash (Youtube in Firefox) and Spotify (running under Wine). These output via the analogue output.

I understand how I can change the 'general' audio output to HDMI if I'm running Gnome, but obviously it's XFCE. Could someone give me a pointer on how I can get all audio to use HDMI?

Thanks in advance!

Will

---

### Post by iitywygms on 2010-05-02
go to setup and change the audio settings output device to ALSA:plughw:0,3

in terminal do
sudo nano ~/.asoundrc

and add this line

defaults.pcm.device 3

save then reboot.

Hope this helps.  It works for me.

---

### Post by JugeHuge on 2010-05-03
I have used these steps that i have described on other thread.
[HDMI audio setup]("http://ubuntuforums.org/showpost.php?p=9220267&postcount=18")

---

### Post by stormb on 2010-05-11
> **iitywygms said:**
> go to setup and change the audio settings output device to ALSA:plughw:0,3

in terminal do
sudo nano ~/.asoundrc

and add this line

defaults.pcm.device 3

save then reboot.

Hope this helps.  It works for me.

This sorted it, thanks!

---

### Post by uopjohnson on 2010-08-19
Thanks iitywygms I think you just saved me a couple of hours of looking around for that.

---

### Post by Twigathy on 2010-12-10
Bit of a thread res, but instead of rebooting you can simply do this:
/etc/init.d/alsa-utils restart

Saves a reboot and preserves precious uptime :-)

---

