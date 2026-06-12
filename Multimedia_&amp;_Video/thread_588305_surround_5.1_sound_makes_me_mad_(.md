---
title: "surround 5.1 sound makes me mad :("
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by pompos on 2007-10-23
Hey...
I tried today if I had 5.1 sound with my linux machine. Unfortunately I discovered that mplayer was just working in a 2 channel mode :(
So I searched the internet and found the following commands to enable/force 5.1 sound in Kmplayer.```
ao=alsa:device=ch51dup
channels=6
```
Besides a rubbish surround sound (more to it later) it caused quite a trouble on my PC with the sound processing programs. When I was playing a 6 channel file the soundcard got blocked for all the other programs. Thus it wasn't going through some sound daemons :(
However... when I played a DVD with 6 audio channels I have got the feeling, that my soundcard or its driver didn't check that I just want to have 5.1 and not 7.1 surround sound. For instance, my rear right speaker was silent, while my rear left was behaving as the center was supposed to.
I did some testing with speaker-test and it resulted in the same mixed up channel mess.```
speaker-test -c 6 -D surround51
```


I'd be very very thankful if somebody could help me with my problems.

P.S. With KMix I am able to control the volume of every single speaker of my 5.1 speaker set.

EDIT:
My "soundcard" is an onboard Realtek ALC888 on the [Gigabyte 965P-DS3 (rev3.3)](http://www.gigabyte.de/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2430&ProductName=GA-965P-DS3)

---

### Post by disturbed1 on 2007-10-23
Your channel mappings are wrong. Look here [http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml]("http://www.cse.ohio-state.edu/%7Ebondhugu/alsamch.shtml")

and also search these (Ubuntu) forums for the mapping and .asoundrc configuration. It's, unfortunately, a known problem with some on board sound codecs.

---

### Post by xpd777 on 2007-10-23
Nice mini-how to. haven't tried it though.


anyway, my question is more of a follow-up.

what if i play a file that's ac3 encoded how will it play then with the asounrc set to replicate the front stereo to the rear stereo speakers?

---

### Post by xpd777 on 2007-10-23
Iv tried everything already from this website 

[http://www.cse.ohio-state.edu/%7Ebondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/%7Ebondhugu/alsamch.shtml)

my asoundrc


> # for 5.1 speakers
pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}


my rc.local

> # vi /etc/rc.local
...
echo Setting 5.1 Channel volumes... 
amixer -q set Master 100% unmute  
amixer -q set PCM 40% unmute  
amixer -q set Surround 100% unmute  
amixer -q set Center 81% unmute  
amixer -q set LFE 100% unmute  
amixer -q set "Surround Jack Mode" "Shared"  
amixer -q set "Mic select" "Mic2"   
amixer -q set "Mic" 65% unmute  
amixer -q set "Channel mode" "6ch"   
amixer -q set "Center/LFE Down mix" 100% unmute 
amixer -q set "Duplicate Front" mute   


my ICH4 copied from > [http://www.cse.ohio-state.edu/%7Ebondhugu/ICH4.conf](http://www.cse.ohio-state.edu/%7Ebondhugu/ICH4.conf)

i still cant get a sound on my front center speaker.


my alsa mixers all UNmute and 100% full volume. even from the alsamixer in the terminal

---

### Post by pompos on 2007-10-25
i got it working :D

```
pcm.ch51dup {
         slave.pcm "surround51"
         slave.channels 6
         type route
	 ttable.0.0 1 #front left
	 ttable.1.1 1 #front right
	 ttable.2.4 1 #rear left
	 ttable.3.5 1 #rear right
	 ttable.4.2 1 #center
	 ttable.5.3 1
}

```

I still have to convince KMPlayer to use that profile but console mplayer does whats it supposed to do.

HOWEVER, there is still a problem. When one program is using 3D sound its blocking the soundcard for all the other programs :( Is there a way to get rid of that ego behaviour?

---

### Post by eheyl on 2007-10-26
I'm trying to get my 5.1 to work as well. I just came across this thread and am reading the  ohio state page, but my question is (i'm less than a week old with ubuntu) where/how do I find the .asoundrc? 

thanks!!
Erik
Got my multifunction printer working, now just this and I'm WUNderbar!

---

### Post by eheyl on 2007-10-26
I've got a quickie general question as well: There's a folder that apparently I don't have access to as a regular user and I want to delete it. Is there any way to changer permission without invoking the command line? In Mepis there was the option to open as root when you right clicked but there doesn't seem to be that here.

---

### Post by eheyl on 2007-10-26
Alright I've run the sound test and can hear all my channels in the correct order.

---

