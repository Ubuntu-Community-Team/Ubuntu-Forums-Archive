---
title: "Mythbuntu and HDMI or SPDIF audio"
date: 2009-06-19
forum: Mythbuntu
---

### Post by agentsmith23 on 2009-06-19
Is it possible to use HDMI or SPDIF audio in Mythbuntu? I had an Asus M3N78-EM mobo wich had both built in and neither would work in mythbuntu but I could get HDMI or SPDIF to work in VLC or any other audio/video program that I could specify the audio source. I am returning it and getting a Gigabyte GA-MA78GM-US2H, it also has HDMI and SPDIF audio out. I have looked for a way to specify the audio source but I can't seem to find it. Is it possible? Please help!

Thanks,
Dave

---

### Post by ian dobson on 2009-06-20
Hi,

In the mythfronend configuration, there's an option to configure the audio output to use (AudioOutputDevice). Per default this is set to ALSA:default so you need to configure the default output for ALSA to point to your SPDIF output or change the Parameter to point to the SPDIF output.

Have a look here:- [http://www.mythtv.org/wiki/Configuring_Digital_Sound_with_AC3_and_SPDIF](http://www.mythtv.org/wiki/Configuring_Digital_Sound_with_AC3_and_SPDIF)

Regards
Ian Dobson

---

### Post by ikke2808 on 2009-06-20
Take a look here: [http://wizandchips.wordpress.com/2009/03/22/how-to-upgrade-alsa-the-easy-way/](http://wizandchips.wordpress.com/2009/03/22/how-to-upgrade-alsa-the-easy-way/) 

I ran it to enable audio over HDMI and it works fine. 
Only downside is that I have to repeat is every time the kernel is touched by an update.

It takes a while, but after the neccessary reboot all works fine.

Cheers,

Frank.

---

