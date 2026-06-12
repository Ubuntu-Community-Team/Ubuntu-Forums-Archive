---
title: "Problem with a2dp"
date: 2009-10-27
forum: Multimedia Software
---

### Post by vinayg1986 on 2009-10-27
i am trying to stream audio to my jabra bluetooth headset...
i have configured all the files such as asound.conf, .asoundrc, .a2dprc.
i am using mplayer for streaming........

when i include:

pcm.bluetoothraw {
   type bluetooth
   device 00:1D:82:XX:YY:ZZ
}
pcm.bluetooth {
    type plug
    slave {
        pcm bluetoothraw
    }
}

in .asoundrc and use the command

**mplayer -ao alsa:device=bluetooth test.wav**

The file plays in the headset w/o any error.....

But when i include :

pcm.a2dpd {
              type a2dpd
}

in the .asoundrc and necessary things in .a2dprc and use the command

**mplayer -ao alsa:device=a2dpd test.wav**

i can see the file streaming progress w/o any error in PC but i'm not able to hear anything in the headset.......

Can anyone please guide me regarding this problem..............

Thanks in advance............

---

### Post by vinayg1986 on 2009-10-27
The last two lines of my .a2dprc is:

# Your bluetooth headset address
address=00:1D:82:XX:YY:ZZ

# Address of your alsa output (default : plughw:0,0) you have to know what to do
alsaoutput=

Am I supposed to add anything after alsaoutput=  ????

---

