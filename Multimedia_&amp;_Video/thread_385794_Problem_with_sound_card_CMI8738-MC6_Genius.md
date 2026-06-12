---
title: "Problem with sound card CMI8738-MC6 Genius"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by gaiterin on 2007-03-16
Hi!
I have the sound card [Genius Sound Maker Value 5.1]("http://www.geniusnet.com/geniusOnline/online.portal?_nfpb=true&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fcategory%2FqueryPro&_windowLabel=productPortlet&productPortletproductId=278439&_pageLabel=productPage&test=portlet-action").
I used more Linux distros (Ubuntu 6.1, Kubuntu 6.1, Mandriva 2007, suse 10.2), and alls identificate the card as "[c-media cmi8738-mc6]("http://www.cmedia.com.tw/?q=en/PCI/CMI8738")".

THE PROBLEM IS:
- Without the .asoundrc file in my home directory, I can't hear sound in the central and subwoofer speakers.
- And with the .asoundrc file below, I can't hear sound in the left and right speaker.
- I always hear in the back left and back right speakers, disabled in the kmix "Four channel".

I like hear all speakers, and in surround.
( In Windows XP I haven't any problem. I hear it perfect, but I need install the driver and a Mixer. If I don't install the mixer, I hear as linux without .asoundrc file ).

I [readed]("http://www.mythtv.org/wiki/index.php/Asoundrc_CMI8738-MC6") more about this [problem]("http://alsa.opensrc.org/Cmipci"), i tried more .asoundrc files, but they can't work!

Help please! ;)
Thanks very much.



#My .asoundrc file is:
# 6 channel dmix:
pcm.dmix6 {
    type dmix
    ipc_key 1024
    ipc_key_add_uid false
    ipc_perm 0660
    slave {
        pcm "hw:0,1"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 5120
    }
}

# upmixing: 
pcm.ch51dup {
    type route
    slave.pcm dmix6
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

pcm.duplex {
    type asym
    playback.pcm "ch51dup" # upmix first
    capture.pcm "hw:0"
}

# change default device:
pcm.!default {
    type softvol 
    slave.pcm "duplex"
    control {
        name "Software Master"
        card 0
    }
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

---

### Post by Lord Illidan on 2007-03-16
You probably have a motherboard with an internal soundcard, which is being recognised by Linux instead of the Genius one.

---

### Post by gaiterin on 2007-03-16
Yes.
I have a VIA sound card.
I tried to deactivate it in the BIOS, but Linux also recognizes it :( Why?
Thanks!
Marcos.

---

### Post by Lord Illidan on 2007-03-16
Then you are not disabling the soundcard properly or else it's a bigger problem.

Can you chose a different soundcard from the Volume Control Preferences?

Also, what does lspci and dmesg tell you? Post their output here.

---

### Post by gaiterin on 2007-03-16
Yes, I can change the sound card in kmix.

I don't undertand this:
"Also, what does lspci and dmesg tell you? Post their output here."
I use Linux from only 2 months.

I think try desactivate with a swith in the mother board, not in the Bios.
Thanks!
Marcos.

---

### Post by Lord Illidan on 2007-03-16
My bad. I should have explained further.

Open up a terminal [ALT + F2 : and run konsole] and type lspci and paste here the output which it gives you. Do the same thing with dmesg.

---

### Post by gaiterin on 2007-03-16
a

---

### Post by Lord Illidan on 2007-03-16
Are you sure you have a Genius soundcard??

---

### Post by gaiterin on 2007-03-16
Yes. All Linux distros (Ubuntu 6.1, Kubuntu 6.1, Mandriva 2007, suse 10.2), and alls identificate the card as "c-media cmi8738-mc6".
I have got this sound car:
[http://www.geniusnet.com/geniusOnline/online.portal?_nfpb=true&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fcategory%2FqueryPro&_windowLabel=productPortlet&productPortletproductId=278439&_pageLabel=productPage&test=portlet-action](http://www.geniusnet.com/geniusOnline/online.portal?_nfpb=true&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fcategory%2FqueryPro&_windowLabel=productPortlet&productPortletproductId=278439&_pageLabel=productPage&test=portlet-action)
I'm sure.

I think that is a problem bios... it not disable the sound card :( I find the jumper in the mother board... in the manual appear... BUT IN THE MOTHER BOARD the jumpers are soldiers :S
Thanks

---

### Post by gaiterin on 2007-03-17
Hi.
I can disable the mother board's sound card modify the jumpers of harware :D
Now, I sure that I only have the Genius (C-media) sound card.
In the kmix only appear the c-media.
But... the sound is equal :(
(Now I haven't the .asoundrc file)

Can be have the solution this webs?
[http://alsa.opensrc.org/Cmipci#4.2F6_Multi-Channel_Playback](http://alsa.opensrc.org/Cmipci#4.2F6_Multi-Channel_Playback)
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=.&chip=CMI8338%2C+CMI8738%2C+CMI8768&module=cmipci](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=.&chip=CMI8338%2C+CMI8738%2C+CMI8768&module=cmipci)

I tried to change the kmix values... but don't surround :(
Any idea?
Thanks very much! ;)
Marcos.

You can see the screen shoots of my kmix, Amarok and sound card configuration in:
-Kmix:
[http://img152.imageshack.us/my.php?image=snapshot4gr7.png](http://img152.imageshack.us/my.php?image=snapshot4gr7.png)
[http://img296.imageshack.us/my.php?image=snapshot5tx1.png](http://img296.imageshack.us/my.php?image=snapshot5tx1.png)
[http://img218.imageshack.us/my.php?image=snapshot6pj4.png](http://img218.imageshack.us/my.php?image=snapshot6pj4.png)
-Amarok:
[http://img296.imageshack.us/my.php?image=snapshot7fy2.png](http://img296.imageshack.us/my.php?image=snapshot7fy2.png)
- Configuration harware:
[http://img150.imageshack.us/my.php?image=snapshot8gs8.png](http://img150.imageshack.us/my.php?image=snapshot8gs8.png)

---

### Post by gaiterin on 2007-03-17
Hi!
It works!!!! :D
The configuration is the last posted by me.
And I put this .asoundrc file in my home:
Thanks very much Lord Illidan!!!!!! :D ;)

The key is: Disabled the sound card of the mother board by the jumpers, NOT by the Bios!
Config the kmix and Amarok as me.
And this asoundrc file:

# 6 channel dmix:
pcm.dmix6 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:0,1"
rate 48000
channels 6
period_time 0
period_size 1024
buffer_time 0
buffer_size 5120
}
}

# upmixing:
pcm.ch51dup {
type route
slave.pcm dmix6
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

pcm.duplex {
type asym
playback.pcm "ch51dup" # upmix first
capture.pcm "hw:0"
}

# change default device:
pcm.!default {
type softvol
slave.pcm "duplex"
control {
name "Software Master"
card 0
}
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

---

### Post by Lord Illidan on 2007-03-17
I didn't help that much, to be honest. Great that you worked hard to solve it.

---

### Post by gaiterin on 2007-03-17
Hi.
Now, I hear perfect the sounds system, and amarok...
but not a sounds of movies! ?:O
The main change was disabled the integrated sound card.
When I like watch a movie (.avi) or dvd, the kmplayer or kaffeine display this error:
Audio output unavailable. Device is busy.

Any idea?
Thanks very much!
Marcos.

---

### Post by gaiterin on 2007-03-17
Uhmmm... If I config Kaffeine or Kmplayer as Xine sound 2.0 (it was configured as 5.1), it works!
But, I like the 5.1 sound for the movies...
What's the problem?
:O Marcos.

---

### Post by gaiterin on 2007-03-18
Hi!
The solution is go to the KDE Control Center under Sound System, there's an Auto-Suspend setting that defaults to 60 seconds. Put to 1 seconds.
It's works! :D
Marcos.

---

### Post by Lord Illidan on 2007-03-18
Or disable the sound system in KDE.

---

### Post by gaiterin on 2007-04-09
Hi!
I find a error now :(

In the Flash Webs (youtube...etc), the sound not works in user mode. If I enter as root mode, it works.

If I delete the file .asoundrc in my home, it works, but I lose the 5.1 sound.

I try changed the attributes (root -> user of the folder "Plugings" in "usr/lib/firefox"), but when I restart, it always is root.

I have got the folder /home/mozilla/firefox too.

Help please!

Thanks!
Marcos.

---

### Post by rabid9797 on 2007-04-13
im having the same problem with the same card..no sound in firefox(but i have an option of choosing between the VIA and CMI card)

---

### Post by goldan on 2007-10-07
well i have  cmi8738-6CH i tried what you posted
it didnt worked queit well but got me further then i've ever got
so i mixed it up with my .asoundrc
removed some stuff
and then i got STEREO to SUORROUND
So thank you very much
i'm on fiesty 7.04
here's my .asoundrc

#this is from your file which gaved me stereo to sorround
# 6 channel dmix:
pcm.dmix6 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:0,1"
rate 48000
channels 6
period_time 0
period_size 1024
buffer_time 0
buffer_size 5120
}
}

# upmixing:
pcm.ch51dup {
type route
slave.pcm dmix6
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}
#this is what i added which gaved my surround in ac3 movies
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

---

### Post by gaiterin on 2007-10-07
Perfect the last entrie of Goldan! :)
With this asoundrc file, works soundrround and the flash applications/video :)
Thanks very much ;)
Marcos.

---

### Post by goldan on 2007-10-08
I cant believe i really halped someone :D
thank you

---

### Post by Vivaldi on 2007-10-10
maybe &#1085;&#1097;&#1075; &#1089;&#1092;&#1090; help to me too. I used your asoundrc - all works fine (5.1 etc) but only in one application (fex I can't start amarok & hear sounds of kopete) does anybody know how to fix it ?

---

### Post by Vivaldi on 2007-10-10
maybe you can help to me too. I used your asoundrc - all works fine (5.1 etc) but only in one application (fex I can't start amarok & hear sounds of kopete) does anybody know how to fix it ?

---

### Post by gaiterin on 2007-10-11
Hi.
Each application has a particular configuration for the audio.
You must search and configure in 5.1 kaffeine, amarok... etc.
;) Marcos.

---

### Post by italoivo on 2007-12-09
with the goldan code the sound works on firefox and the other applications but the rear speakers are not working. with the first code posted the rear speakers works fine but doesn't works with the firefox flash movies.

---

### Post by CyberMoon on 2008-05-12
> **gaiterin said:**
> Hi.
Each application has a particular configuration for the audio.
You must search and configure in 5.1 kaffeine, amarok... etc.
;) Marcos.

I've the same problem in ubuntu 8.04, the asoundrc's code works fine in my genius value 5.1 but dont work in more of one program at same time.

---

### Post by gaiterin on 2008-05-13
Hi.
The asoundrc file not works with Pulse, the new audio control of Ubuntu 8.04.
You must configure ALSA in Preferences/Sound, not Pulse Audio.
Regards.

---

### Post by CyberMoon on 2008-05-13
> **gaiterin said:**
> Hi.
The asoundrc file not works with Pulse, the new audio control of Ubuntu 8.04.
You must configure ALSA in Preferences/Sound, not Pulse Audio.
Regards.

A have all in alsa but i still cant hear multiple sound

---

