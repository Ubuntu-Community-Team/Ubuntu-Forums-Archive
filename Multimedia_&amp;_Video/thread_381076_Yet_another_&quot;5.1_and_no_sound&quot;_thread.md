---
title: "Yet another &quot;5.1 and no sound&quot; thread"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by zeny on 2007-03-10
I've installed ubuntu 6.10, I've got a Hercules card using the CS46xx driver, did I install it? No, as soon as Ubuntu was installed I got sound, no problems there. 
I didn't have 5.1 sound (out of all speakers) so I searched this forum and google. 

Most guides said to edit the asoundrc file, I didn't have one so I just created it and added

This is my /home/mr/.asoundrc file
[HTML]pcm.ch51dup {
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
[/HTML]

Honestly I don't know what to do anymore, I'm not that advanced at linux and would really like some help 

FYI I've read up on these articles
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Hercules&card=Game+Fortissimo+II.&chip=CS4624&module=cs46xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Hercules&card=Game+Fortissimo+II.&chip=CS4624&module=cs46xx)
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)
[http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)

and a few others, so far nothing works

PS. I also have a onboard sound AC97, it is disabled in BIOS at the moment
I tried it earlier but it also had no 5.1 comming out however I didn't configure anything for it as I would perfer to use my hercules card

Thanks!

---

### Post by johnc4510 on 2007-03-10
Try this page for help:
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sound&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sound&titlesearch=Titles)

Hope this helps. The wiki has all kinds of instructions for different areas of ubuntu

---

### Post by zeny on 2007-03-10
Great thank you!

when I do this 

speaker-test -Dplug:surround51 -c6 -l1 -twav

it works, I can hear from all the speakers now, however no applications seem to pick it up as even login to audio programs only use 2.1

---

### Post by johnc4510 on 2007-03-10
Go to: System>Preferences>Sound
Click on the Sounds Tab and look at the bottom of the window and make sure the default sound card is set correctly.

---

### Post by zeny on 2007-03-11
its blank, and won't let me select anything

---

### Post by zeny on 2007-03-12
I've tried doing asound set-default-card command then did a reboot still doesn't show, anyone got any ideas, I even tried configuring certain applications for it as I searched the net and still no luck, so the 5.1 works just ubuntu doesn't reconize it or something

---

### Post by zeny on 2007-03-14
Ok, I've done a few more things and tried almost everything, even at one point lost my sound completly, I'm now back where I was with a different asoundrc file, if ANYONE has gotten 5.1 to work with their apps please let me know! I feel like I'm so close because I can hear sound out of all of them during the sound test that I posted just above, its all about getting the programs and system to do it now!

Thank you to anyone who posts back!!!

---

### Post by Kubular on 2007-03-15
I'm having trouble getting my sound sorted too. What do you have in your asoundrc script?

I'm using a different card/chipset but it'd be interesting to see what you've done.

---

### Post by zeny on 2007-03-15
this is what I got now, however it doesn't work =\

```

# front channel
pcm.FRONT {
type hw
card 0
device 0
}

ctl.FRONT {
type hw
card 0
}


# rear channel
pcm.REAR {
type hw
card 0
device 1
}


# center_lfe channel
pcm.CENTER_LFE {
type hw
card 0
device 3
}

pcm.SURROUND_51 {
type plug
slave.pcm COMBINE
route_policy default
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 1
ttable.1.5 1
}


pcm.COMBINE {
type multi
slaves [
{
pcm FRONT
channels 2
}
{
pcm REAR
channels 2
}
{
pcm CENTER_LFE
channels 2
}
]
bindings [
{ slave 0 channel 0 }
{ slave 0 channel 1 }
{ slave 1 channel 0 }
{ slave 1 channel 1 }
{ slave 2 channel 0 }
{ slave 2 channel 1 }
]
} 

```

---

