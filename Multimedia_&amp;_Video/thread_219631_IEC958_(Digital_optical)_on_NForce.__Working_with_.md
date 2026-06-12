---
title: "IEC958 (Digital optical) on NForce.  Working with $ aplay but nowhere else."
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by moeFinley on 2006-07-20
I've been using Ubuntu for the last week and I'm determind not to give up with Linux again.

I've dedicated my Shuttle (sn41G2 [www.shuttle.com](www.shuttle.com)) machine to it and everything is going well.  The next step was to connect it to my TV as I did in WinXP.  However I can't playback sound through my optical out.  But I know it's working because I can hear perfect playback using

aplay -Dplug:iec958 "test.wav"

I have the IEC958 volume sliders in the Ubuntu GNome Volume Control window and have tried all the various switches there, but with no luck.

I'm using the standard ALSA drivers and it doesn't seem like a driver problem so I have tried the NVidia drivers.  I'd prefer to keep the system as standard as possible.  Then it is easy to learn the OS on.

If anyone could offer any help I be really greatful.  I'm sure it's something simple I just haven't spotted yet!

Thanks

System Spec:

ShuttleX sn41G2
Mainboard FN41 (NForce2 Chipset)
Audio Realtek ALC 650
ALSA Drivers

---

### Post by moeFinley on 2006-07-22
Can anyone *please* help with this.  I have tried all the advice in the forums and howto guides I could find.  It's seems like it should be something so simple because it is already working with $ aplay??????

---

### Post by jay_cee on 2006-07-22
What applications in particular are you trying to get to work?

---

### Post by moeFinley on 2006-07-22
Well I guess Totem and Rhythmbox would be my priorities.  The optical lead goes off under my floor to my amp for music and movies.  Will it not just output everything to IEC958?

I have tried switching 'Audio output type' to 'AC3 Passthrough' which someone recommended in a forum post.  It didn't make any difference.

Thanks for the reply, I was begining to think nobody was gonna help and that can only mean one of two things.  The question has been asked and answered a million times and people are ignoring you or nobody has ever found a solution and they don't want to be the one to break the bad news!  I'm not sure which is worse :)

---

### Post by jay_cee on 2006-07-23
Yea, I've found this SPDIF stuff to be horrendously documented. Lots of annecdotes to be found on google, but no one really understands what they are doing (like myself).

A couple of random thoughts. I discovered that my SPDIF link (not sure if its my soundcard or my receiver) won't work with 44100 sample rate.

If you do a 'man' on aplay you'll find a rate switch. I would try playing your sample wave file at both 44100 and 48000 so you will understand if your SPDIF link has any sample rate issues. I believe that DVDs are 48000 and CDs and mp3s are at 44100.

It sounds like your link is working to some degree and maybe your apps just aren't choosing the right alsa pcm device. I wish totem gave you a little more info about what "AC3 passthrough" really means. Maybe try some of the other players: mplayer, vlc, kaffeine, etc...will let give you a better idea of what is going on with Alsa. I know that mplayer lets you explicitly call out particular Alsa pcms.

Sorry I can't be of more help. Post your progress. I figure the more "paper trail" the better. There will be someone else tomorrow having the same problems....

---

### Post by moeFinley on 2006-07-23
I managed to get DVD audio to play out of digital in Totem.

It seems not all DVDs are AC3 audio, some use PCM.  I even have one DVD (Black Books) which has PCM in the menus and AC3 in the episodes.  This means the audio comes out of different sources depending what it is!

It's very disapointing if this is the conclusion.  Is this just an issue with specific hardware or across the board?

---

### Post by jay_cee on 2006-07-23
Hmmm...that's interesting. I haven't encountered that. I've probably viewed 60 or 70 DVDs from netflix over the last 6 months. They've all played fine through totem's "AC3 Passthrough" setting. No additional mucking was required.

---

### Post by moeFinley on 2006-07-29
A little update, although sadly not a solution.

I plugged in a Sound Blaster Extigy (USB) which setup instantly and just has a check box in the 'switch' tab for optical out.  Now all my sound goes out though the optical!! :D 

So I guess this means it's not a Linux/Ubuntu thing but just a weird drivers thing? :confused: 

Anyway, like to know more but I'm happy I've got my music!!  Just need to get TV out working now :)

---

### Post by royw on 2007-06-19
Howdy,

I was experiencing the problem described in this thread and found a solution.  I'm running Kubuntu 7.04 so the directions are for KDE.  From System Settings, Sound System, Hardware, check "Override device location" and point it to your digitial output device, in my case it was /dev/dsp1.  You can use "aplay --list-devices" to get a hint for the device number.  My output was:

royw@royw-htpc:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by blue46 on 2007-09-27
i was gonna write the same topic, good that this forum searchs for similar topics right after entering the Title,  very smart feature!

anyway my comp:

Abit AN7  with nforce audio,  it has optical output  and regular analog.   I have logitech Z5500 speakers connected to optical output  and  skype headphones to the analog via minijack.

Anyway  everything was working fine (as you moeFinley would wish)  , which is:

Totem used to play  all movies and mp3 files via my optical output

its because in System-Preferences-Sound  i have selected  Nvidia Nforce2 - IEC958
if i selected  Nvidia Nforce 2 (or autodetect)  the sound was coming out through  analog minijack

But this was only till yesterday  when i wanted to make Totem to play my DVD movies.  So i started to search the internet, installing some drivers, codecs, and now  it plays DVDs , and the sound is from optical


But all other movies and mp3 started going through the analog output now!! :(  i dont know what to do ,  how to force Totem to play the sound through optical output?  
 Obviously i  dont remeber what  did i do ,   is there some restoring feauture in UBUntu,  like i could restore to point from 2 days ago?

i messed it up good completely unnecessary , actually watching DVDs in Ubuntu  is impossible because DVD spins so fast its to loud.  unless there is some software like nerospeed for linux.   hardparm doesnt work for my NEC DVDRW i already tried.

---

### Post by moeFinley on 2007-09-27
I did find a solution which involves editing the ALSA config file.  I don't have the details with me at the moment but I will post them tomorrow.

---

### Post by moeFinley on 2007-09-29
Here's what I did to get all sound going to the optical out.

```
sudo gedit /etc/asound.conf
```
Hopefully this is blank and you can just pasted the following.
```
pcm.card0 {
  type hw
  card 0
}

pcm.dmixer {
  type dmix
  ipc_key 1025
  slave {
    pcm "hw:0,2"
    period_time 0 
    period_size 2048
    buffer_size 32768
    rate 48000
  }
  bindings {
    0 0
    1 1
  }
}

pcm.skype {
  type asym

  playback.pcm "dmixer"
  capture.pcm "card0" 
}

pcm.!default {
  type plug
  slave.pcm "skype"
}
```
The line *pcm "hw:0,2"* is what changes the output to the optical.  If you want to use the normal jack again use *pcm "hw:0,0"*

Once you have saved the file you can restart the ALSA with 

```
sudo /etc/init.d/alsa-utils restart
```

I hope this is what you're looking for.

---

### Post by tkarkache on 2008-06-02
I followed your lead moeFinley to get ouput for ATI HD3870 HDMI on an Intel Q35JO running mythbuntu. And it works! Instead of editing global changes I modified the .asoundrc in my home directory.
But I used card 1 device 3 as was listed in aplay -l.
Watching an MKV in surround now!

Many thanks for the reading on this.
I also read up here.
[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

Cheers!


> **moeFinley said:**
> Here's what I did to get all sound going to the optical out.

```
sudo gedit /etc/asound.conf
```
Hopefully this is blank and you can just pasted the following.
```
pcm.card0 {
  type hw
  card 0
}

pcm.dmixer {
  type dmix
  ipc_key 1025
  slave {
    pcm "hw:0,2"
    period_time 0 
    period_size 2048
    buffer_size 32768
    rate 48000
  }
  bindings {
    0 0
    1 1
  }
}

pcm.skype {
  type asym

  playback.pcm "dmixer"
  capture.pcm "card0" 
}

pcm.!default {
  type plug
  slave.pcm "skype"
}
```
The line *pcm "hw:0,2"* is what changes the output to the optical.  If you want to use the normal jack again use *pcm "hw:0,0"*

Once you have saved the file you can restart the ALSA with 

```
sudo /etc/init.d/alsa-utils restart
```

I hope this is what you're looking for.

---

