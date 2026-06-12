---
title: "Weird sound mixer problems after compiling new kernel"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by the_mouse on 2007-09-30
Hi guys!
I'm using Kubuntu Feisty, but i was experiencing very weird netowrk drops and it turned out it was a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87078") in the linux kernel, so the only solution was compiling a new kernel...

So, I looked around and found [this topic]("http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel+net+lost"), wich was very helpful for me, especially the automated script wich does all the work for me :)

Everything went  all right, but now I have some strange problems with the suond mixer :(

My sound card is 7.1 channel and it's integrated into the mainboard and I have one fornt panel for separate mic and headphones, wich with the old kernel (2.6.20 - the default in Feisty) were all ok and I was able to control the front mic and turn on/off the headphone, regardless  of the other channels :)
[[IMG]http://img216.imageshack.us/img216/6708/snapshot14ek5.th.jpg[/IMG]](http://img216.imageshack.us/img216/6708/snapshot14ek5.jpg) [[IMG]http://img146.imageshack.us/img146/2236/snapshot15as8.th.jpg[/IMG]](http://img146.imageshack.us/img146/2236/snapshot15as8.jpg)

I noticed I can't set the other channels of the sound card, but it was ok, because I have only 2.1 sound system

After installing the 2.6.22.9 Linux kernel, KMIx showd the missing front, center, etc.. channels, but now I dont't have control of the front panel mic and headphones, wich bugs me a little, because I was used to them
Here's how now KMix looks:
[[IMG]http://img216.imageshack.us/img216/8720/snapshot12hu8.th.jpg[/IMG]](http://img216.imageshack.us/img216/8720/snapshot12hu8.jpg) [[IMG]http://img216.imageshack.us/img216/2436/snapshot13og3.th.jpg[/IMG]](http://img216.imageshack.us/img216/2436/snapshot13og3.jpg)

I'll be grateful for everyone who has idea how to "add" the headphone and front mic channels back to KMix
Here's something relly strange - they didn't work on Windows either, but they did on the 2.6.20 linux kernel :(

I checked that the two kernels are using the same module: snd_hda_intel

---

### Post by the_mouse on 2007-10-13
Doesn't anyone has an idea why some of the sound channels disapeared and other showed up?

Recently I installed the 2.6.23 kernel - the same problem as the 2.6.22 :(

---

### Post by the_mouse on 2007-10-15
Hi again, guys! I accidently (!) solved my problem! 
It turned out that there's such option in BIOS (to turn off or on the front sound panel) and it was set to [Auto], I turned it on and the lost channels (front panel headphone and front mic) showed in KMix!

---

