---
title: "Seq24 won't run"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by msjulie on 2006-11-30
Hello Everyone,

I'm running an old Sager Laptop with Ubuntu 6.10.

Things seem to be running normal.

I used Add / Remove to install seq24.

It appeared to install correctly.  I clicked the icon Applications-->Sound & Video-->Seq24.

I also did the 'sudo apt-get install seq24'

It went through its paces and told me I had the most current version.

Still no luck.

I was hoping to give Seq24 a little test run.  I'm just interested in some midi sequencing and some sequence looping.  This looks like the tool I need.

I haven't installed anything yet to setup my keyboard and midi ports yet.  This may be part of the problem.

I was hoping I could at least get the program up and running, but nothing seems to happen after I click the icon.  Well, the hard drive spins a bit, but nothing happens on screen.

Yeah, I'm new to this.  I didn't want go go installing a bunch of unnecessary stuff on my sluggish system.

Just as a check I installed / ran / then removed abiword just to make sure I understood the process and check things out.  That seemed to go well.

Any help would be nice.

Julie

---

### Post by asmok on 2006-12-01
Julie,

just follow documents:

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

1. First basic environment:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

2. Then Jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

3. Then Seq24:

[https://help.ubuntu.com/community/HowToSeq24Introduction](https://help.ubuntu.com/community/HowToSeq24Introduction)

I think nobody can give you more information, those documents are good ones.

Best Regards Asmo Koskinen.

---

### Post by msjulie on 2006-12-01
Asmo Koskinen,

Thank you for your reply.

I have reviewed those documents already, but I will go back and read through them again.

Unfortunately, I was trying to avoid installing too much stuff.  I just wanted to put enough on to make seq24 happy.

If I can't get it up without too much overhead, great.  If not, I'll need to wait until I have a better system--couple months.

I really was just hoping to get some basic MIDI sequencing and playback via my computer and keyboard.  The audio editing and DSSI could wait.

Again, thank you for the reply.  I'll see what I can do.

Julie

---

### Post by sgx on 2006-12-05
Hi, make sure jackd is installed in /usr/bin. Then, if
aconnect
is installed, (in /usr/bin) open a shell, and type
aconnect -i      then
aconnect -o
to see your input, then output music ports.
(aconnectgui    is available for a graphic view.)
Then if qjackctl is installed, it
is a favorite for connecting midi ports and software,
with a tab for midi, and one for audio, just select the
items you want connected, and click the connect button
...or a combo of
kaconnect    and    qaconnect can be installed and used much the same.
You may need to check available kernel sound modules, so type
lsmod
If snd-seq
is not listed, the command
modprobe snd-seq
will enable it for the session, and adding snd-seq
to the text file
/etc/modules
will enable it always. This is for the alsa sequencer, needed for 
sequencing and midi things. Get zynaddsubfx, and vkeybd, the great softsynth for linux, and the handy virtual onscreen midi keyboard, and test them with qjackctl...
start jackd
start qjackctl
start vkeybd
start zynaddsubfx
connect zyn to the alsa_pcm out, 1 and 2
connect vkeybd to zyn
play notes on vkeybd, or find zyns own keyboard button on its
main panel to reveal its own arger virtual keyboard...all this is
only 5 or 8 megs of downloads, and is basic for what you want and need,
plus zyn has a few hundred nice sound to get going with...hope this helps!

---

### Post by msjulie on 2006-12-06
Hello sgx,

Well, I get some time this weekend, I'll check out your suggestions.  I do appreciate it.

I did get vkeybd installed and running without a hitch.  I didn't expect it to play sounds without loading other programs and stuff.  But it loaded and I could press the keys.

I was hoping to do a similar thing in seq24, but it won't even boot for me.

I think I'll need to follow your instructions so that seq24 will have all it needs to run.

It may seem odd, but I wasn't actually concerned at this point in making anything happen.  I just wanted to test drive seq24 to see what it can do (features and feel type stuff.)  I honestly just wanted a minimum install option.

It appears that you may have gotten me on the right path.  Thank you.

Julie

---

### Post by October on 2006-12-09
I'm pretty sure that Seq24 requires jack to run properly.

Quick and easy way, assuming you are hooked up to the internet:

#sudo apt-get install qjackctl jackd
.....

#qjackctl

Press the "Start" button.  With any luck at all it will be up and running.  Then start Seq24:

#seq24

It's a very nice sequencer and worth any trouble if you want to play with MIDI easily :)

---

### Post by msjulie on 2006-12-10
Hello October, sgx, Asmo,

Thank you all for your help.

Special thanks to October for making it sound straight forward, and sgx for the seq-snd info.

seq 24 is up and running.  Thank you all very much.  Now it's time to play!

Julie

---

### Post by sgx on 2006-12-12
> **msjulie said:**
> Hello October, sgx, Asmo,

Thank you all for your help.

Special thanks to October for making it sound straight forward, and sgx for the seq-snd info.

seq 24 is up and running.  Thank you all very much.  Now it's time to play!

JulieCheers!

see recent 'zynaddsubfx causes system crash' thread for
quick/easy how-to running this great synth...
8')

---

