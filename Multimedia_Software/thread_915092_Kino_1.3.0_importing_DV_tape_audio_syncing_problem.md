---
title: "Kino 1.3.0 importing DV tape audio syncing problem"
date: 2008-09-09
forum: Multimedia Software
---

### Post by Eviljim on 2008-09-09
Hello,

I am relatively new to Ubuntu and have virtually transferred my day to day use from Windows to Ubuntu. :)

Now whilst I have managed to get everything I want from Vista either running under wine or finding an opensource alternative, Kino is my main problem.

You see I am trying to capture footage from my Sony camcorder onto a internal HDD. 

Now, I can sort out the raw1394 issue, can capture the source and save it as an avi file, except when I go to play it back, the audio is terribly out of sync with the video.

I have played back the same video in Vista and its definately the file and not the playback program.

So for the time being I have to keep Vista to be able to use Nero Recode/Vision.

Now I haven't tried running Nero under wine, as I believe that this can be sorted out, and I now a big advocate of opensource and don't really want to use a temporary workaround like wine/Nero.

Oh, the file size varies between 4.1 and 10.2GB in size and I have tried DV type 1 and DV type 2 with and without OpenDML and all options lead to the same result.

Any suggestions welcome.

PC Spec.

Intel E6700 Dual core ovc to 3.2GHz,
Ati 2600XT, Ati 8.4 driver
2GB RAM
750GB HDD (500GB + 250GB)
Separate firewire card.
On board Intel HD soundcard using ALSA driver.


Cheers for any tips/pointers

---

### Post by Eviljim on 2008-09-15
Any ideas anyone?

---

### Post by mjpoetic on 2008-09-20
I am experiencing the same problem.  I will report back with what I have found on the net to help.

---

### Post by Mesqueeb on 2009-01-11
Can anyone help me aswell?
I use KINO, but all my videos I import into Kino are **offsync**... like a half second. The sound and video are not synchronized. It's only the DV file, not the avi.
Does anyone has the same problem or a solution?
Thank you!

-Mesqueeb

---

### Post by aquamammal on 2009-02-14
Same problem.


Horribly off sync. Is there any way to edit this? I don't even ask that I can reimport it. I just want to drag the audio back a second.

Thanks

---

### Post by DuncanNZ on 2009-02-23
Interesting problem you guys are having. Could it be that the machine is short on processor power while capturing?

Also, I've just updated the instructions on [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) and would love it if you could take a look and let me know if you hit any problems. I'll try and help you in this thread.

---

### Post by Sea_Anemone on 2009-07-13
Just wanted to add something to this, in case someone else has this issue. I to had a problem where it appeared the timing was off, and i started to do a bit of digging. Turns on, in dv format, its quite unlikely for this to happen, more likely its a delay playing back. Anyway, this link says it all. Kudos to ddennedy for the original suggestion.   Worked like a charm.
[http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=3187](http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=3187)
In short;

In Kino, go to :  Edit -> Preferences -> Audio tab. Set audio device tab to /dev/dsp.


now, where's my damned Nemo?

Sea_A.

---

### Post by gavinstewart on 2009-08-08
Changing the audio device to /dev/dsp worked immediately. Thanks a lot.

---

### Post by umechanism on 2011-03-27
I changed mine from, "default" to "/dev/dsp" and now the video plays at about 2x speed with zero audio.  This is a DV file that I've already captured from my camera.  How do I resolve this?  :confused: Anyone?

---

