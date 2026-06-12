---
title: "Bluetooth headphones not working (Ubuntu 15.10)"
date: 2015-11-24
forum: Multimedia Software
---

### Post by cascadia_adam on 2015-11-24
Hello,

        I recently bought a pair of bluetooth headphones (Skullcandy Hesh 2 Wireless Headphones), which are having trouble connecting to my laptop (Lenovo Thinkpad T450S with Ubuntu 15.10 installed)

The headphones are fine - they pair with the bluetooth on another computer alright. I have a dual boot on my laptop with Windows 10, and they've worked on there alright, so I doubt it's an issue with my bluetooth hardware.

Ubuntu seems to pair with the headphones, but when I go into the audio settings to select the headphones under audio input, no sound plays after I select my headphones. Usually, the audio settings freezes up shortly afterward.

I had gotten them to work for about two months, but now they're messing up again. I'm not exactly sure what got them working initially (or what has them messing up again). My only guess is that shortly before they started working for the first time, I was prompted with a 'allow access' window which I haven't seen since. It was something similar to what appears when you pair a device which requires a pin (however, this window didn't ask for a pin). I haven't seen this window again and don't know how to prompt it. Perhaps I'm having issues with the pin?

I've tried nearly every option without any luck (setting up as headset, audio sink, etc.) and tried both audio options in audio settings (A2DP Sink, HSP/HFP). I've tried changing settings in the /etc/bluetooth folder, without any luck. Also, I've updated and installed everything I could relating to bluetooth for Ubuntu. I tried installing blueman, but had no luck there either. I've also updated everything possible thing related to bluetooth with no luck.

Any suggestions? Any tests I can run, so I can provide you useful output from my computer?

Any help would be greatly appreciated. I'm new to Ubuntu and don't quite know my way around yet.

Thanks!
Adam

---

### Post by cascadia_adam on 2015-11-24
Not sure if this is useful, but a few times when I've first paired the headphones, there is about 3-4 seconds of distorted audio that comes through, before it shuts off altogether.

When I go into sound settings, the options for balance, fade, and subwoofer are greyed out. Changing the mode doesn't help at all.

---

### Post by cascadia_adam on 2015-11-24
So this Ubuntu noob got lucky and somehow I managed to fix it (I still have no idea how). In case it's useful to anyone else with the same setup, here's what I did:

After uninstalling some things I shouldn't, I had to do a clean install of Ubuntu 15.10. Maybe not the easiest first step, but I messed some things up and had to do it.

After it was back up and running, I added AutoEnable=true to /etc/bluetooth/main.conf. It still didn't work, so I tried installing Blueman. And now it works. I have no idea why, but it's connecting as A2DP sink, whereas before it would only connect under the HSP/HFP setting.

If anyone else has this problem, best of luck to you!

---

