---
title: "How do I troubleshoot sound?"
date: 2014-06-17
forum: Multimedia Software
---

### Post by sofasurfer on 2014-06-17
I started reading the sound troubleshooter at [https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_1](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_1)

First off, it wants me to issue commands for "pulse". The first command... :~$ killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*
results in this message... rm: cannot remove &#8216;/home/daryl/.pulse*&#8217;: No such file or directory

I have pulse on my system (Ubuntu 14.04)... :~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
so why did the command fail?

This is as far as I have gone so far.

I was wondring if I am supposed to run the multimedia troubleshooting guide which I used to always run on my installations? However, I think that is not needed on new versions...is it?

In case your wondering what my problem is, I am getting feedback, or bleed over, from my mouse and keyboard on my speakers. The sound is a dull rumble with click (sometimes). The volume controls do not effect it bleed over. I have checked my connections and isolated my speaker wires for the mouse and keyboard reciever wires.

Is there a special troubleshooting or sound-setup guide I should use?

This problem started before I installed 14.04. It started on 12.04 after someone bumped the computer. So I do not believe it is a software problem. But I wonder if the card got damaged and how do I test it through commands?

Sure hope someone can help me out.

---

### Post by Bucky Ball on 2014-06-17
You want to completely remove Pulse? Do you have Pulseaudio Volume Control installed (pavucontrol)?

Please use [code] tags. Makes the output much clearer and easier to read. Thanks.

---

### Post by sofasurfer on 2014-06-17
My post above tells what my problem is. I have mouse, keyboard and cursor bleedover in my speakers and no sound from sources.
I would post outputs from commands if I had an idea what commands to run.

---

### Post by Bucky Ball on 2014-06-17
Understood. Yes, I seem to be having the same issue with my laptop. I just started using it with powered speakers a few days ago, mini jack from the headphone socket into a mixer then out to speakers. Is this similar to your setup, particularly the powered speakers? I thought I might need to grab some balanced cables rather than the ancient dodgy things I have, but they work fine with other devices. 

I'm curious and will be playing around with that a bit later so will post anything that might be useful ... :-k

PS: I presume the sound is fine if you plug in headphones?

---

### Post by sofasurfer on 2014-06-17
> **Bucky Ball said:**
> mini jack from the headphone socket into a mixer then out to speakers. 
PS: I presume the sound is fine if you plug in headphones?

Old powered speakers plugged directly into PC speaker minijacks. Headphones plugged into same minijacks have same issue. Front mini jacks for headphones are damaged from quite a long time ago. Not sure if they have function or not. 

Off to work. Any help you can give me will be appreciated. Will check back later, m
aybe from work.

Thanks

---

### Post by sofasurfer on 2014-07-07
I have fixed my problem...almost. I replaced my motherboard. Bought a MSI H61M-P31 if that means anything to you...It doesn't to me.
My sound now works again. The motherboard must have been damaged. 
Anyway, now I have sound but it is a low level volume and it seems to be lacking range...meaning that it seems to need a equalizer adjustment.
I have the volume up on my panel and on the source I am listening to and I also topped it out under sound settings>output volume.
Do I need to install an equalizer or is it already there someplace?
Please advise.
Thanks.

---

### Post by Bucky Ball on 2014-07-08
> **sofasurfer said:**
> I have the volume up on my panel and on the source I am listening to and I also topped it out under sound settings>output volume.


Volume up on the panel? You mean you have turned the speaker icon up full?

The source you are listening to? Which software are you using?

Do you have Pulseaudio Volume Control installed? Have a look for it, play some music and click the 'Output' tab in PAvolume control. It's in the software centre (or Synaptics) or in a terminal:

```
sudo apt-get install pavucontrol 
```

Experiment with that if you haven't already.

* You are playing a file from your hard drive using music player software?

---

### Post by sofasurfer on 2014-07-10
SOLVED...
I read so many posts and tutorials and nothing gave me a working equalizer. Then I stumbled onto this...  [https://wiki.archlinux.org/index.php/PulseAudio](https://wiki.archlinux.org/index.php/PulseAudio)
Just go down to the equalizer section and run 3 simple commands. Worked like magic.

---

### Post by Bucky Ball on 2014-07-10
Excellent and good find. Please share the fix with the community and mark the thread as solved to help future travelers.

Enjoy. ;)

---

### Post by sofasurfer on 2014-07-10
I read many threads and tutorials and was not able to get a working equalizer on my ubuntu 14.04 installation. I found this wiki tutorial. Tons of great help. A section on equalizer which sets one up with 3 commands. [https://wiki.archlinux.org/index.php/PulseAudio](https://wiki.archlinux.org/index.php/PulseAudio)

---

### Post by Bucky Ball on 2014-07-10
Threads merged. The solution should be here, not on a separate thread. ;)

If I find a solution after a long thread I've started myself I often edit the first post and direct people to the post with the fix in it at the beginning of the post. You might like to do the same.

Good luck.

---

### Post by sofasurfer on 2014-07-10
Thanks

---

