---
title: "recording from line in (x fi titanium)"
date: 2010-11-30
forum: Multimedia Software
---

### Post by asvestomix on 2010-11-30
hello, I have the sound card creative X-Fi titanium, normally in windows 7 i used to record from an external pre-amplified microphone and just pass the sound trough line-in.. How can i do the same In ubuntu? By the way i tyred to install the creative drivers ([http://support.creative.com/Downloads/welcome.aspx](http://support.creative.com/Downloads/welcome.aspx)) but I couldn't make it any ideas?

---

### Post by asvestomix on 2010-11-30
Bump!

---

### Post by asvestomix on 2010-11-30
bump

---

### Post by cchhrriiss121212 on 2010-11-30
Try using either sound recorder, or Audacity. Also try to leave it a day before bumping, other people's requests are just as important as yours.

---

### Post by asvestomix on 2010-11-30
Sorry about the bump, .. the recorder isn't working since it cant find the proper recording port .. i tried to install the driver that creative gives but i had some authorisation problems when i tried to run the "make install" command, in read-me they say to run it as root how should i do this?

---

### Post by cchhrriiss121212 on 2010-11-30
You should not need to install any drivers manually as all functionality will be built into the OS via kernel modules. And the screenshot you gave indicates that the capture port is functional. 
Could you try using Audacity to record? Set the capture device with Edit>Preferences>Devices. If it fails please post the error messages.

---

### Post by asvestomix on 2010-11-30
I tried it also  with AUDACITY it gave no error(exept if i put it to mono, see my attached pics) it just dont detect any sound is like i connected an muted microphone, maybe it is because i am connecting it to the line in port that is actually microphone also, in windows i had to switch it to line in mode to work or the sound would be distorted. Sorry if i get annoying ,

---

### Post by cchhrriiss121212 on 2010-12-01
Double check that you are connecting this to the right port, and that you have a good signal going into the line in.

You could also try opening alsamixer from a terminal, then check the capture level.

---

### Post by asvestomix on 2010-12-01
> **cchhrriiss121212 said:**
> Double check that you are connecting this to the right port, and that you have a good signal going into the line in.

You could also try opening alsamixer from a terminal, then check the capture level.
Thank you for answering chris, yeas the mic is right connected , if i boot from windows it records like it should but in ubuntu it is like the driver not support completely my sound card. how can i open the aslamixer and check as you said?

---

### Post by cchhrriiss121212 on 2010-12-01
> how can i open the aslamixer and check as you said?
Go to Accessories>Terminal then type in alsamixer and press enter. Use left and right to select a channel and up and down to change volume.

According to this thread the card captures OK, and you can set what recording source to use using alsamixer:
[http://ubuntuforums.org/showthread.php?t=1594505](http://ubuntuforums.org/showthread.php?t=1594505)

---

### Post by asvestomix on 2010-12-01
Hello, the alsa mixer allowed me to set the 'line-in" as capture device instead "S/PDIF-in" that was before, in programs like audacity i don't have those options like the alsamixer to set the line-ine as Recording device i only have "Creative X-Fi:Front/WaveIn (hw:0,0)", "Pulse" and "Default" as recording options, but  then i went to system>Preferences>sound>input and chose "0332 analog mono" as input device then i tried in audacity to set the recording device as "pulse"  and then i had sound.. i dont know if is that correct i think  it should probably work with "Creative X-Fi:Front/WaveIn" port, By the way what is pulse?

---

### Post by cchhrriiss121212 on 2010-12-02
> i dont know if is that correct
The correct setting would be whatever works, so I would not worry about doing the right thing the wrong way, I think I use the "default" setting on mine. Just make a note of whatever settings work for you, in case you upgrade or reinstall.
> By the way what is pulse?
Pulse is the sound server for Ubuntu. It works "on top" of ALSA. Here is what we get if we imagine audio as a chain of communication:
Sound card > ALSA > Pulse > Software

So when you record audio this is the specific route your audio data takes:
Creative X-fi > ALSA > Pulse > Audacity

This is why we have to check ALSA and pulse configuration when troubleshooting audio. In a simpler OS there would just be one layer between the hardware and user software.

---

### Post by asvestomix on 2010-12-02
> **cchhrriiss121212 said:**
> 

This is why we have to check ALSA and pulse configuration when troubleshooting audio. In a simpler OS there would just be one layer between the hardware and user software.

I made a mistake in my old post, the sound wasnt came from my mic it was from my usb cam so it didnt work. Is there a way to check the configuration for pulse just like i did for alsa?
By the way thank you for helping me so far

---

### Post by cchhrriiss121212 on 2010-12-02
There is a program called pavucontrol which I think you will need to download. Try and get get pulse to recognise the X-fi as the default card, then try Audacity again.

---

### Post by asvestomix on 2010-12-02
hello, from pavucontrol I tried from there any device and any profile available but nothing gave back any audio except the usb camera with it's internal microphone. The curious thing here is that every time i make a change to sound card's mode from the pulse audio volume control it change automaticly the capture device from alsamixer from Line-in to Mic.

---

### Post by asvestomix on 2010-12-02
i think i should install the driver that creative gives, here is the Current release features:

    * ALSA PCM Playback
    * ALSA Record
    * ALSA Mixe
I think this could help me resolve the problem, but i am following the instructions and i can't get it installed, please check my attachments files to see details.

---

### Post by asvestomix on 2010-12-04
any ideas guys?

---

### Post by cchhrriiss121212 on 2010-12-04
I also tried to install that driver and I get the same error you do, probably because it is 2 years old. But like I said it should not even be necessary. Unfortunately I don't have any other ideas on how to get this working. 

You should try submitting a bug report on Launchpad, Ubuntu has regressions in hardware compatibility every release, and I would say this is one of them.

---

