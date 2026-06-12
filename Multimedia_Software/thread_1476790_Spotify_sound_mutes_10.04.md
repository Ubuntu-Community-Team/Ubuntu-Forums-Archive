---
title: "Spotify sound mutes 10.04"
date: 2010-05-08
forum: Multimedia Software
---

### Post by JD1994 on 2010-05-08
Hi, hope you can help :D,

Having a few issues with spotify (running through wine)

I load spotify up, and have changed the configuration of wine to use the ALSA(?) drive to stop the sound from being jumpy etc. 

However after my recent upgrade to 10.04 lucid, everytime i load spotify the opening sound plays and then when i click play on ANY song the sound (for the whole computer) mutes.

Its quite annoying as it means i have to press play then unmute and turn up the volume (as the volume turns down as well).

Once again, hope you can help!
John

---

### Post by Ferio on 2010-05-09
Similar issue round here, although my problem doesn't got solved with your solution; it's happened me twice: the 1st time it implied re-installing, and the 2nd one has been half an hour ago, and I can't find any other solution. I think I won't use Spotify for a while...

---

### Post by JD1994 on 2010-05-09
To be honest i don't actually have a solution. Its just unmuting of the computer sound, which quite frankly is a) annoying and b) efforrt!

I might wait until i get the new version of spotify and see what happens, unless i get a response from someone that has the answer to my problems! :(

---

### Post by JD1994 on 2010-05-12
Well it seems to have fixed itself... Basicly make sure youre using ALSA sound thing.
Presumably the update fixed the issue? i dunno. But its sorted!

---

### Post by Ferio on 2010-05-12
> **JD1994 said:**
> Well it seems to have fixed itself... Basicly make sure youre using ALSA sound thing.
Presumably the update fixed the issue? i dunno. But its sorted!

Mine hasn't fixed, at least for this very morning; it happens when using Flash (YouTube), when listening music in Rhythmbox, when seen videos in Totem...

---

### Post by JD1994 on 2010-05-13
> **Ferio said:**
> Mine hasn't fixed, at least for this very morning; it happens when using Flash (YouTube), when listening music in Rhythmbox, when seen videos in Totem...

Yeah mine used to do that in 9.04 jaunty however now it doesn't :D

basicly try 
> padsp winecfg
And on the audio section make sure you have the OSS audio flagged.

Then run spotify through the command:
> padsp wine "C:\Program Files\Spotify\spotify.exe"

That seemed to fix it for me... although i haven't been using it for long so there could be some bug still lurking in the darkness.
Try it out and let me know :)

---

### Post by Ferio on 2010-05-14
It doesn't work for me :( It's weird because my problem is that digital sound output turns on after some random time using the analogic one, that gets turned off.

---

### Post by sidewalk on 2010-05-14
I'm also having problems with Spotify stopping to play music under Wine in Ubuntu 10.04.

I have a clean install of Ubuntu 10.04, so I don't have old 9.10 settings or such.

For me it works for a day or two, then it stops playing. The track bar just doesn't go beyond 0 seconds. It doesn't help to restart the program.

The only solution I currently have for this issue is to reboot the machine.

I'm thankful for all help that you guys can provide.

---

### Post by kallebas on 2010-05-14
> **JD1994 said:**
> Yeah mine used to do that in 9.04 jaunty however now it doesn't :D

basicly try 

And on the audio section make sure you have the OSS audio flagged.


It started working for me doing the opposite =) (Changing from OSS to ALSA in winecfg)

---

### Post by tookyourtime on 2010-05-22
It worked for me to switch to ALSA, but the sound quality is appalling compared to OSS

---

### Post by homerhomer on 2010-05-28
There's some versions of wine in the the PPA that have been patched for pulse audio. It would be worth a short to see if that give better results. 

good luck

---

