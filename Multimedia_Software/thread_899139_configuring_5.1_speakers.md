---
title: "configuring 5.1 speakers"
date: 2008-08-24
forum: Multimedia Software
---

### Post by theguitarfreak on 2008-08-24
Hi guys, I am absolutely new to ubuntu and i cannot configure my 5.1 speakers (i have onboard 5.1 sound controller). I came across a post where a guy was talking about some code but i couldnt make out properly what to do. Can someone plz tell me the step by step procedure? Again, i am absolutely new to linux and ubuntu.

---

### Post by theguitarfreak on 2008-08-24
Can anyone plz tell me how to configure 5.1 speaker system in ubuntu? I am absolutely new to linux, so plz help

---

### Post by overdrank on 2008-08-24
Hi and welcome, please do not create multiple threads on the same issue. :)

---

### Post by theguitarfreak on 2008-08-24
> **overdrank said:**
> Hi and welcome, please do not create multiple threads on the same issue. :)

Im sorry but the previous thread i created got no replies to it and i couldnt find it to continue it

---

### Post by overdrank on 2008-08-24
> **theguitarfreak said:**
> Im sorry but the previous thread i created got no replies to it and i couldnt find it to continue it

Hi and you can find you thread by using the search, find all your post. If not answered you can bump it after 24 hrs. :)

---

### Post by Chris Musampa on 2008-08-24
I had the same problem, now solved:
[http://ubuntuforums.org/showthread.php?t=886807](http://ubuntuforums.org/showthread.php?t=886807)

---

### Post by theguitarfreak on 2008-08-25
pcm.!default {
    type             plug
    slave.pcm       "softvol"
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "ch51dup"
    }
    control {
        name        "All"
        card        0
    }
}

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5
}

I used the above code in a text file and saved it as .asoundrc in my home folder. But still i dont get sound from my rear speakers. I am using amarok player.

---

### Post by Chris Musampa on 2008-08-25
Check all sliders are up in your mixer (you should also have a new slider named "All").
Check that 'surround jack mode' is set to 'shared'
Check that amarok is using 'default' for its stereo device.

---

### Post by theguitarfreak on 2008-08-27
> **Chris Musampa said:**
> Check all sliders are up in your mixer (you should also have a new slider named "All").
Check that 'surround jack mode' is set to 'shared'
Check that amarok is using 'default' for its stereo device.

Im using GNOME ALSA Mixer. There isnt any new slider named "All" as you are saying and i have put a tick on "Sorround Jack Moder" in the mixer.

---

### Post by Chris Musampa on 2008-08-28
The above worked for me (I use kde rather than gnome, not sure why that should make any difference), the new slider appeared in kmix after a reboot.  Sorry I can't offer you anymore advice guitarfreak as I'm also fairly noob.

---

### Post by theguitarfreak on 2008-08-28
Getiing sounds from all the speakers finally but aint getting proper channel controls in the mixer. And when i am interchaning the rear and center/subwoofer jack, i am getting better bass frequencies.

---

### Post by Chris Musampa on 2008-08-28
> **theguitarfreak said:**
> Getiing sounds from all the speakers finally but aint getting proper channel controls in the mixer. And when i am interchaning the rear and center/subwoofer jack, i am getting better bass frequencies.

I guess your sound card outputs are numbered differently to mine, try experimenting with the ttable section of your .asoundrc

My outputs are:
0 = front left
1 = front right
2 = rear left
3 = rear right
4 = center
5 = subwoofer

to make a bit clearer how the ttable thing works:

pcm.ch51dup {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1          # route front left to front left, full volume
ttable.1.1 1          # route front right to front right, full volume
ttable.0.2 1          # route front left to rear lef, full volume
ttable.1.3 1          # route front right to rear right full vol
ttable.0.5 0.5        # route front left to subwoofer, half vol
ttable.1.5 0.5        # route front right to subwoofer, half vol
}

The above doesn't give any centre output on my setup, if I wanted I would add
ttable.0.4 0.5        # route front left to centre, half vol
ttable.1.4 0.5        # route front right to centre, half vo


Hope this helps.

---

