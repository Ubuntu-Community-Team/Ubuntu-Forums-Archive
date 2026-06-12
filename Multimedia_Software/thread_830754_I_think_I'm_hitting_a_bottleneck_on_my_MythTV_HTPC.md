---
title: "I think I'm hitting a bottleneck on my MythTV HTPC..."
date: 2008-06-16
forum: Multimedia Software
---

### Post by Cadmus on 2008-06-16
I've got an old Dell Optiplex with the following spec
[LIST]
[*]P4 1.8GHz
[*]256MB memory (might be 512)
[*]nVidia 5200 128MB card
[*]400GB PATA HD
[/LIST]

I've got standard ubuntu Hardy running on it and the restricted nvidia driver happily displaying to a TV through S-VIDEO as well as a monitor on a coffee table, VLC's been able to play fullscreened mkv and avi files on the main screen with only the occasional hiccup (such as if a torrent programs doing a final verification).

Yesterday I installed a [DVB-T]("http://en.wikipedia.org/wiki/DVB-T") card ([Hauppauge WinTV Nova-T PCI]("http://mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI")) and found that during playback it would skip/burble a little on the audio, but otherwise be ok, VLC was showing 25/30% usage on both CPU and Memory. I could ascribe the skipping to using the onboard audio routed into the TV.

The real performance issues happenned after I installed MythTV. Tuning in takes a couple of seconds but that's fine, however video and audio playback are both stuttery and occasionally changing channels causes Myth to stop playback with the message
```
Error was encountered while displaying video
```
I've done the solution described [here]("http://www.mythtv.org/wiki/index.php/Troubleshooting:Error_was_encountered_while_displaying_video") but that's not totally solved the problem.

Can anyone point me in the right direction of finding out what my bottleneck is? I have a feeling that using regular Ubuntu combined with a PATA disk is what's giving me grief, but what ese could it be.

---

### Post by Cadmus on 2008-06-17
I don't like bumping, but I wasn't able to make any headway last night.

---

### Post by Erlander on 2008-06-17
I suspect that the specs of your pc are not up to DVB decoding.

Try installing Kaffeine and see if it is any better.  Its very easy to get going and is a good test program.  Me TV is another possibility.

both are in the repositories.

Rob

---

### Post by Cadmus on 2008-06-18
Thanks! As I said using VLC playback was much smoother, so it's not so much the decoding of DVB (I think I could sort that with some judicious pruning/use of a more lightweight WM) but rather the consequent saving to disk and redisplaying MythTV requires.

I could try adding some more memory but to be honest I think It's time for "Cadmus HTPC 2.0" the energy efficient Dual-Cores have plumetted in price so it might be time to switch to something with a little more grunt and a SATA disk.

---

### Post by Erlander on 2008-06-18
The copying of a broadcast stream to disc does not require very much in the way of pc power.  The data as broadcast in a digital stream is what is recorded so it is just writing to disc.  Watch your hard disc light and you will see its not busy all the time but in bursts.

The real work for a pc with dvb is the turning of the digital signal into video.  With an accelerated graphics card much of this work is done by the gpu but with a low end card it finishes up being done by the cpu.

Try recording a stream and then playing it back.  The pc works harder on playback than when just recording.

To make matters worse in my opinion the linux drivers are not as good as Windows and even quite powerful display cards do not perform as well as they should in linux.

rob

---

