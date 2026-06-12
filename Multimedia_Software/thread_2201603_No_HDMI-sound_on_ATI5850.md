---
title: "No HDMI-sound on ATI5850"
date: 2014-01-25
forum: Multimedia Software
---

### Post by boeingx37 on 2014-01-25
Hello. I have Acer Aspire 8942g and ATI 5850m and ALC670. My hdmi sound didn't work at all.
After I add this record GRUB_CMDLINE_LINUX="radeon.audio=1" and  alsa driver.
I used these commands for it.
 sudo add-apt-repository ppa:ubuntu-audio-dev/alsa-daily
    sudo apt-get update
    sudo apt-get install oem-audio-hda-daily-dkms
hdmi-output came out, twisting a sound-wheel a hear sound about changing of loudness , but the point is when I press "Test Sound" or try to play a movie I hear silence.
Please help me out.

---

### Post by boeingx37 on 2014-01-25
This is what alsamixer tells about hdmi

---

### Post by Bigpat on 2014-01-25
The best thing I can say into remove [COLOR=#000000]alsamixer [/COLOR]and re-install it and then follow the above instructions. I have done all the above and I was finally able to get my ATI HDMI 4550/4350 sound working after 4 @#$!# days. The Ubuntu form rocks.My only issue sis now that is I cannot get my headphones to automatically select when i plug them in I have to manually select it every time. My second issues is that I get no sound in Google Chrome from HDMI at all for no videos even in you tube. I only get sound in Google chrome through the head set. Make sure you have alsa-base install along with alsa-utils check with the synaptic package manager and just type in the search alsa and see what you have installed.

---

### Post by Yellow Pasque on 2014-01-26
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by boeingx37 on 2014-01-26
> **Bigpat said:**
> The best thing I can say into remove [COLOR=#000000]alsamixer [/COLOR]and re-install it and then follow the above instructions. I have done all the above and I was finally able to get my ATI HDMI 4550/4350 sound working after 4 @#$!# days. The Ubuntu form rocks.My only issue sis now that is I cannot get my headphones to automatically select when i plug them in I have to manually select it every time. My second issues is that I get no sound in Google Chrome from HDMI at all for no videos even in you tube. I only get sound in Google chrome through the head set. Make sure you have alsa-base install along with alsa-utils check with the synaptic package manager and just type in the search alsa and see what you have installed.
Thank you for your answer. I'll try it out now!
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
Thank you for you answer too! I attached report from the first link(I did it with plugged hdmi-wire up)
And this is all what I got from the second link(seems pulseaudio didn't installed)
alex@alex-Aspire-8942G:~$ echo autospawn = no >> ~/.config/pulse/client.conf  #use ~/.pulse/client.conf on Ubuntu <= 13.10
alex@alex-Aspire-8942G:~$ killall pulseaudio
alex@alex-Aspire-8942G:~$ LANG=C pulseaudio -vvvv --log-time=1 > ~/pulseverbose.log 2>&1
Now, again, I checked my hdmi-sound.
When I connected hdmi to my TV I only hear sound of changing of loudness(gurgling) for the second time twisting the sound-wheel.
The "Test sound" and playing of movies keep silent as before. But if I watch a video from YouTube. I hear sound with the horrible noise. And when I went to watch other video from YouTube after a couple of minutes. There was no sound.(So I have to re-plug hdmi up).
So hdmi works but really really buggy:(

---

### Post by boeingx37 on 2014-01-26
I'm sorry for a stupid question but how to update alsa because these cpmmands killed my sound at all. Nothing works.
[COLOR=#000000]**sudo**[/COLOR] apt-add-repository ppa:ubuntu-audio-dev[COLOR=#66CC66]/[/COLOR]ppa
[COLOR=#000000]**sudo**[/COLOR] [COLOR=#000000]**apt-get**[/COLOR] update
[COLOR=#000000]**sudo**[/COLOR] [COLOR=#000000]**apt-get**[/COLOR] upgrade

---

### Post by Yellow Pasque on 2014-01-26
For the alsa info, you're supposed to copy/paste the link it gives you.

For the pulseaudio log, it will leave the log in your home directory. You have to attach it.

---

### Post by Bigpat on 2014-01-26
[COLOR=#000000][COLOR=#000000]**sudo**[/COLOR][/COLOR][COLOR=#000000] apt-add-repository ppa:ubuntu-audio-dev[/COLOR][COLOR=#66CC66]/[/COLOR][COLOR=#000000]ppa was successful however 
however [/COLOR][COLOR=#000000][COLOR=#000000]**sudo**[/COLOR][/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000][COLOR=#000000]**apt-get**[/COLOR][/COLOR][COLOR=#000000] update and [/COLOR][COLOR=#000000][COLOR=#000000]**sudo**[/COLOR][/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000][COLOR=#000000]**apt-get**[/COLOR][/COLOR][COLOR=#000000] upgrade was a no go.

it says 

[/COLOR] Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Yellow Pasque on 2014-01-26
1. Remove that ppa from your sources. It's not actively maintained and doesn't have any packages for Saucy or later.
2. Since all your sound devices are HDA compliant, upgrading drivers is easy: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
3. After you do step 2, reboot and run alsa info again. Copy/paste the link that it gives.
4. Get the pulse log. There will be a file in your home directory after you run the commands.
```
tar cvf pulselog.tar.gz  ~/pulseverbose.log
```
5. Attach pulselog.tar.gz here.

---

### Post by Bigpat on 2014-02-01
Here is my logs for pulse audio and I even include the Alsa as well.

---

### Post by tho.tran1809 on 2014-02-03
I also have problem with HDMI sound, ATI card.

Look forward for helps!
Thanks!

---

### Post by Yellow Pasque on 2014-02-03
I don't have any magic answers. I do notice some error messages which look suspicious:
```
[   17.561869] hda-intel 0000:01:00.1: Using LPIB position fix
[   17.561925] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   17.564372] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[   17.604851] HDMI ATI/AMD: no speaker allocation for ELD
```

---

