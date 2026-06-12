---
title: "NEW -- mythchanger firewire channel changer"
date: 2008-11-10
forum: Mythbuntu
---

### Post by majoridiot on 2008-11-10
there have been a lot of issues with firewire channel changing with mythtv... mostly due to
too many different and cobbled-up versions of channel changers.  there have also been a lot
of issues with channel changers failing after STB firmware updates- mostly with Scientific 
Atlanta STBs.

instead of trying to keep on top of all of the changes with the various changers, i have put 
all of the different methods into one changer.  most of the source comes from both *mythprime* 
and *scanfw*, with a bit of new code added at the request of a tester (thank you, kevin conover).

the only argument required is the channel number- everything else *should* be automatic for 
most users... however:

for scientific atlanta owners- if your STB is detected incorrectly or fails the channel change, 
try forcing another SA changer with the -f option.  the changer required depends on the 
firmware version of your STB and the firmware does not always match the STB model.  try each 
SA changer one at a time until you find the one that works for you.

also, for users recording from more than one STB, a new option (-g) has been added which 
will allow you to tune the STB by supplying the GUID of the target.  otherwise, mythchanger 
will change the channel on the first STB found on the firewire bus.

power-on and bus reset options are also included for the sake of completeness... you may 
or may not find them handy.

source code can be downloaded from here: [https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

a makefile is included for easy compile and installation.  see the included README for 
complete details.

ENJOY!

---

### Post by JBaugh on 2008-12-06
Thank you!  I must say I have been trying to get the channel changer working for my DCH-3200 via command line for quite a while, and this worked right out of the gate.  I would also like to use this opportunity to thank you for all of your other invaluable postings on this forum, I have used them countless times, though never replied.

I did have to use the -f 6 flag to manage this, but here are the vendor and model ID of my STB (DCH-3200)
```
node 1: vendor_id = 0x00001106 model_id = 0x00000000

```

Thanks again!

---

### Post by patrick0605 on 2008-12-06
I'm a bit of a newbie to mythbuntu, but what exactly is this?  I only ask because I'm using the firewire ports on my SA STB for recording.  I have no problem changing channels though.

---

### Post by majoridiot on 2008-12-06
> **patrick0605 said:**
> I'm a bit of a newbie to mythbuntu, but what exactly is this?  I only ask because I'm using the firewire ports on my SA STB for recording.  I have no problem changing channels though.

mythchanger is only needed if:

mythtv fails to change the channel on your stb; or

you need an external channel changer for recording with a capture card

it is a consolidation of the various channel changers from mythtv contrib and elsewhere.
sounds to me like you are fine the way you are... ;)

---

### Post by majoridiot on 2008-12-06
> **JBaugh said:**
> Thank you!  I must say I have been trying to get the channel changer working for my DCH-3200 via command line for quite a while, and this worked right out of the gate.  I would also like to use this opportunity to thank you for all of your other invaluable postings on this forum, I have used them countless times, though never replied.

I did have to use the -f 6 flag to manage this, but here are the vendor and model ID of my STB (DCH-3200)
```
node 1: vendor_id = 0x00001106 model_id = 0x00000000

```

Thanks again!

glad it solved some problems for you.  external changers have been frustrating for some people.

a new version has been posted that should alleviate the need for forcing a changer.  you can download
it from the link above.

---

### Post by crez79 on 2008-12-10
First off, thank you for your work. As a Windows Media Center convertee, I was thrilled and amazed how easy setting up firewire capture.

I have everything for my DCH-6416 working well capturing and changing channels. I have firewire capture set up as well as s-video to a tuner for the encrypted channels, which scanfw helped weed out perfectly. My only issue is if I record a show on the channel the stb is already tuned to. (For example, if I record a show on ch 144 and then later a show on ch 144 without changing the channel to another one.) What happens is everything changes and records right, but the stb displays a guide looking screen. It times out after a certain amount of time, but it makes it look less cool. I can repeat this every time if I use the command via terminal. If I press "exit" on the stb remote, it goes away instantly.

My question is, is there any way around this? I don't know if there is a command to send the "exit" command? That would make the mini guide disappear on channel changes too, which isn't that big of a deal because it only lasts 3 seconds. If there isn't a way to send the "exit" command is there a workaround? I was thinking maybe try to tell it to change to a channel before sending the final channel change, but I don't really know how, and it isn't very elegant.

Again, thank you.

---

### Post by majoridiot on 2008-12-10
> **crez79 said:**
> First off, thank you for your work. As a Windows Media Center convertee, I was thrilled and amazed how easy setting up firewire capture.

I have everything for my DCH-6416 working well capturing and changing channels. I have firewire capture set up as well as s-video to a tuner for the encrypted channels, which scanfw helped weed out perfectly. My only issue is if I record a show on the channel the stb is already tuned to. (For example, if I record a show on ch 144 and then later a show on ch 144 without changing the channel to another one.) What happens is everything changes and records right, but the stb displays a guide looking screen. It times out after a certain amount of time, but it makes it look less cool. I can repeat this every time if I use the command via terminal. If I press "exit" on the stb remote, it goes away instantly.

My question is, is there any way around this? I don't know if there is a command to send the "exit" command? That would make the mini guide disappear on channel changes too, which isn't that big of a deal because it only lasts 3 seconds. If there isn't a way to send the "exit" command is there a workaround? I was thinking maybe try to tell it to change to a channel before sending the final channel change, but I don't really know how, and it isn't very elegant.

Again, thank you.

funny you should post this, as i discovered a similar thing last night while testing with scanfw on 
my DCT-6212.  the firmware on my stb was updated yesterday, so i was not sure if the timing was 
coincidental or not.

however, both mythchanger and scanfw share common code, so i am not too surprised to see this issue 
pop up here...

i only had a few minutes to poke around last night, so i am not sure if this is a bug or what. i will
look into this sometime in the next couple of days.  in the meantime, sorry for the inconvenience
and sit tight for new source... ;)

---

### Post by crez79 on 2008-12-10
Wow. 30 minutes. I've waited on hold longer. Thanks for looking into it. Great job.   :D

---

### Post by majoridiot on 2008-12-11
ok... i have spent quite a bit of time today trying to track down the breakage here.  by every appearance,
this is due to updates to at least some motorola STB firmware.  the code worked flawlessly on my 
STB until it was updated a couple of days ago (to fix interference from my cell phone on HD channels!).

the changer works fine with 2 digit numbers but causes weirdness if you re-tune a 3 digit channel that
is currently tuned.  i have been through the latest firewire AVC panel specification that i have and the
packet sent to the STB is constructed correctly per that spec... so obviously someone at motorola 
dropped the ball on this one... or someone needs to send me a spec more recent than the 2002
copy i have. ;)

i hacked around with trial-and-error but could not come up with a fix... possibly because there is not
one so long as the firmware is broken.  an additional "select-key" workaround is kinda sloppy, so i
am skipping that for now.

on the plus side, forcing the single-channel method (-f 7) works fine... at least for me.

since i have no clue as to the status of various firmwares across cable providers, i do not know
how many people are affected by this breakage.  for now, i will leave things alone and suggest
that anyone suffering this problem simply add -f7 to their command line.  if this turns out
to be a widespread issue, i will change the source to select the single channel method by default.

if you would like to do this yourself, all you need to do is change line 198 of *mythchanger.c* from:

```
STBS[stb].changer = 6;
```

to:

```
STBS[stb].changer = 7;
```

then make clean, make and sudo make install.

sorry for the hassles... but it looks like this one is outta my hands.  i will play with it more
when time allows.

---

### Post by crez79 on 2008-12-11
Adding -f7 to the command line works for me. Thanks for the quick fix!

---

### Post by majoridiot on 2008-12-17
source code for mythchanger version .10f beta has been posted at: [https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

changes include:

added vendor and model info for new moto and sa stbs

default motorola channel changer is now the single-digit method (7)

if you experience issues with your motorola stb with changer 7, you can force the "fast" changer with -f 6.

if the new changer affects you, please email me... i am trying to sort out where the various firmwares
are being deployed. my email addy is in the README.

---

### Post by Chuffinora on 2008-12-24
Is there any reason why this script might not work with a Hauppauge HDPVR?

I am trying to set-up a new MythTV box, with HDPVR and Rogers SA3250 STB.

I followed the HDPVR wiki and with my channel change script set to /bin/true live TV works.

I can run Mythchanger from command line  mythchanger -f2 -c128 tunes my STB to channel 128 etc.

When I try to change channels with myth by using "mythchanger -f2"  in my mythtv-setup channel change configuration, live tv no longer works.

Here is the log output I get:-


2008-12-24 15:16:37.609 Spawning LiveTV Recorder -- begin
2008-12-24 15:16:37.610 TVRec(1): Changing from None to WatchingLiveTV
2008-12-24 15:16:37.613 TVRec(1): HW Tuner: 1->1
2008-12-24 15:16:37.649 Channel(/dev/video0) Error: GetCurrentChannelNum(128): Failed to find Channel
2008-12-24 15:16:37.649 Channel(/dev/video0)::TuneTo(128): Error, failed to find channel.
2008-12-24 15:16:37.649 TVRec(1) Error: Failed to set channel to 2. Reverting to kState_None
2008-12-24 15:16:37.649 TVRec(1): Changing from WatchingLiveTV to None
2008-12-24 15:16:37.650 Spawning LiveTV Recorder -- end
2008-12-24 15:16:37.650 GetEntryAt(-1) failed.
2008-12-24 15:16:37.650 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-12-24 15:16:37.651 TV Error: HandleStateChange(): LiveTV not successfully started
2008-12-24 15:16:37.651 We have a RingBuffer
2008-12-24 15:16:37.651 TV Error: LiveTV not successfully started

Stupid question, but could someone confirm "mythchanger -f2"  without the "" is the correct syntax  (I have tried "mythcahnger",  and "mythchanger -f2 -c" as well but with same results) to use in the channel change script box in mythtv-setup.

---

### Post by jdoggman on 2009-02-02
Hello all,

I have been having no luck with firewire channel changing and mythtv.  Well, some luck, the problem is that I can record with firewire and change the channel on the box (dch 6200) but it all locks up if I hit a 5c'd channel.  

I would like to record to either analog (coax or S) on my pvr-250 but change  channels on the dch6200 via firewire.  I have tried to use the 6200ch and some other things I have read about with no success. It must be something I am doing or not doing for that matter.  Could someone post an example of the channel change argument used in the setup portion of mythtv? 

I am running on a 64 bit machine, could this be making any difference? I have a  fresh install of mythbuntu 8.1 and this is the only sticky bit so far.  Thanks for all of your help guys!

---

### Post by majoridiot on 2009-02-02
> **jdoggman said:**
> Hello all,

I have been having no luck with firewire channel changing and mythtv.  Well, some luck, the problem is that I can record with firewire and change the channel on the box (dch 6200) but it all locks up if I hit a 5c'd channel.  

I would like to record to either analog (coax or S) on my pvr-250 but change  channels on the dch6200 via firewire.  I have tried to use the 6200ch and some other things I have read about with no success. It must be something I am doing or not doing for that matter.  Could someone post an example of the channel change argument used in the setup portion of mythtv? 

I am running on a 64 bit machine, could this be making any difference? I have a  fresh install of mythbuntu 8.1 and this is the only sticky bit so far.  Thanks for all of your help guys!

mythchanger should do exactly what you need.  after downloading and compiling/installing, test it 
out to make sure everything works:

```
$ mythchanger -c XX
```

where XX is the channel to change to.

there are issues with some moto firmware, so be sure to test to see if you have this issue- change 
the stb to a 3-digit channel and then, using mythchanger, change it to the *same* channel.

if the channel tunes ok, then no problems. if it display a menu or other weirdness, you need to force 
changer #7 by adding -f 7 to the command line.

once it tests ok, the basic command line for mythbackend is:

```
mythchanger -c
```

or

```
mythchanger -f 7 -c
```

if you have to force the changer.

---

### Post by jdoggman on 2009-02-03
Works great! Thank you for all your help! 

I did have an anomaly of sorts; I can use the coax along with the FW channel changer, but had no luck pairing it with the s-video setup.  It would be better to get the upgraded signal, but not necessary. 

If there is anything I can do to help, please let me know. ;)

Now on to that pesky remote...

---

### Post by majoridiot on 2009-02-03
> **jdoggman said:**
> Works great! Thank you for all your help! 

I did have an anomaly of sorts; I can use the coax along with the FW channel changer, but had no luck pairing it with the s-video setup.  It would be better to get the upgraded signal, but not necessary. 

If there is anything I can do to help, please let me know. ;)

Now on to that pesky remote...

it should be as simple as setting the input for the capture card to s-video and putting the mythchanger command
in there too...

note that mythchanger command goes into the cap-card setup in backend setup- *not* in the firewire tuner section.
you want mythtv to change the channel with firewire but record with s-video, so *both* need to be in cap card setup.

no reason it shouldn't work... tests fine with both my pvr-150s using whatever input i select using mythbuntu x64 8.04.

good luck...

---

### Post by reel on 2009-02-06
I attempted to use your code on my 4250HDC and had no success (thanks for putting it out). I have tried both firewire ports on the box and the reset and power on options of your software. I also tried to do -f to all the other Scientific Atlanta options. Below is the typical output from a channel change. It seems to work according to the output. It properly detects and reports my model. Nothing happens on the box though. I suspect that this may be a firmware difference. My box is provided by Brighthouse Networks in Central Florida. Is there anything I can do to troubleshoot this? 

I have never tried firewire to the cable box before so I have no reason to know that channel changing works. One thing I can confirm is that I was able to do Live TV via firewire on mythtv when I had the cable box manually tuned to a channel. Thanks for your help.

I am using mythbuntu 8.10 64bit and it appears that the code compiles and executes without a problem. I am using the onboard firewire port of my motherboard Asus P5Q-EM. Let me know if you need any other information.

# mythchanger -v -c 3

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x1cea Model ID: 0x10cc, Scientific Atlanta Model SA4250HDC


1 STB(s) found:
-------------
STB 1: port=0, node=1, changer=3, GUID=0x001cead43b9a0000

---

### Post by majoridiot on 2009-02-06
> **reel said:**
> I attempted to use your code on my 4250HDC and had no success (thanks for putting it out). I have tried both firewire ports on the box and the reset and power on options of your software. I also tried to do -f to all the other Scientific Atlanta options. Below is the typical output from a channel change. It seems to work according to the output. It properly detects and reports my model. Nothing happens on the box though. I suspect that this may be a firmware difference. My box is provided by Brighthouse Networks in Central Florida. Is there anything I can do to troubleshoot this? 

I have never tried firewire to the cable box before so I have no reason to know that channel changing works. One thing I can confirm is that I was able to do Live TV via firewire on mythtv when I had the cable box manually tuned to a channel. Thanks for your help.

I am using mythbuntu 8.10 64bit and it appears that the code compiles and executes without a problem. I am using the onboard firewire port of my motherboard Asus P5Q-EM. Let me know if you need any other information.

# mythchanger -v -c 3

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x1cea Model ID: 0x10cc, Scientific Atlanta Model SA4250HDC


1 STB(s) found:
-------------
STB 1: port=0, node=1, changer=3, GUID=0x001cead43b9a0000

if none of the SA changers work when trying to force a changer, then either your stb has firmware issues (becoming more
common, sadly) or it could possibly be your firewire chipset.

i would try picking up a cheap firewire card- the cheapies work best in my experience, believe it or not... you should
be able to pick up a via-based card (VT6306 chipset works well) for $15-20.

if still no love changing channels, definitely the firmware... it's no coincidence that STB firmware is getting flaky
firewire-wise, while the cable cos are desperately pushing their crappy DVRs at outrageous prices. ;)

---

### Post by Cyberai on 2009-02-14
Does Mythchanger also verify that a STB has a clear and functioning firewire connection? I have 3 Motorola STB's and have an ongoing problem with them losing their firewire connection at random. If Mythchanger also does a Mythprime to insure the STB is online, then you are indeed a god amongst men MI.

---

### Post by majoridiot on 2009-02-14
> **Cyberai said:**
> Does Mythchanger also verify that a STB has a clear and functioning firewire connection? I have 3 Motorola STB's and have an ongoing problem with them losing their firewire connection at random. If Mythchanger also does a Mythprime to insure the STB is online, then you are indeed a god amongst men MI.

it does not prime, sorry. i kept it a changer-only app so as not to unintentionally interfere... not knowing
what each user's end-use might be.

it would be easy enough to do what you want, however.  wrap the changer command in a bash script and call that from
mythv for channel changing.  i am not sure what sort of issues you have with the stbs going off-line, so relying
on the changer failing as indication that the stb is unstable is not a guarantee... you might be able to do the
channel change but still have an un-primed box.

my recommendation follows... assuming you are targeting the stb by GUID:

command for mythtv-backend channel changer parameter would be something like:

```
primechange $channel GUID
```

where GUID is the manually-entered GUID of the target stb.  each tuner entry should correspond to the correct 
GUID for that stb.

if myth is changing a channel, you know it will likely be recording and want to make sure it is primed... 

primechange script pseudo-code would be something like:

```
$CHANNEL=$1
$GUID=$2

if{
mythchanger -c $CHANNEL -g $GUID  (and any other arguments you might run it with)
}

returns ok, exit

else:

mythprime -c <your safe priming channel> (and any other arguments you might run it with)

mythchanger -c $CHANNEL -g $GUID

```

that would be your best bet... but with a potential down-side: if it does encounter and unstable stb and primes,
it would likely interrupt any recordings in-progress on the other stbs, as they are all primed blindly by mythprime.
it was intended to be run when starting/restarting the backend only, so was written to prime everything, and not
individually.

if that is an issue for you, i can add the prime by GUID code to mythprime when i have the chance.  feel free
to email me if this is the case and i'll see what i can do.

---

### Post by Cyberai on 2009-02-14
> **majoridiot said:**
> it does not prime, sorry. i kept it a changer-only app so as not to unintentionally interfere... not knowing
what each user's end-use might be.

it would be easy enough to do what you want, however.  wrap the changer command in a bash script and call that from
mythv for channel changing.  i am not sure what sort of issues you have with the stbs going off-line, so relying
on the changer failing as indication that the stb is unstable is not a guarantee... you might be able to do the
channel change but still have an un-primed box.

my recommendation follows... assuming you are targeting the stb by GUID:

command for mythtv-backend channel changer parameter would be something like:

```
primechange $channel GUID
```

where GUID is the manually-entered GUID of the target stb.  each tuner entry should correspond to the correct 
GUID for that stb.

if myth is changing a channel, you know it will likely be recording and want to make sure it is primed... 

primechange script pseudo-code would be something like:

```
$CHANNEL=$1
$GUID=$2

if{
mythchanger -c $CHANNEL -g $GUID  (and any other arguments you might run it with)
}

returns ok, exit

else:

mythprime -c <your safe priming channel> (and any other arguments you might run it with)

mythchanger -c $CHANNEL -g $GUID

```

that would be your best bet... but with a potential down-side: if it does encounter and unstable stb and primes,
it would likely interrupt any recordings in-progress on the other stbs, as they are all primed blindly by mythprime.
it was intended to be run when starting/restarting the backend only, so was written to prime everything, and not
individually.

if that is an issue for you, i can add the prime by GUID code to mythprime when i have the chance.  feel free
to email me if this is the case and i'll see what i can do.

I was thinking something like this wrapper would be more reliable as far as knowing if the recording was actually occurring or not:

```


psuedo-code..


mythchanger -g <GUID> -f 6 -v -c <channel>

# Check if the firewire is primed

      test-mpeg2 -r 1 > /tmp/testcap.ts &
       sleep 1
       killall test-mpeg2
       if [ -s /tmp/testcap.ts ] ; then
               echo "#################"
               echo "# Firewire is primed!!!!!!!!!!!!"
               echo "################"
               rm -f /tmp/testcap.ts
       else
               mythprime -v
       fi

```

You could of course, set the entire test under a set of conditions so that it runs until the recording starts properly, or after 5 attempts it fails and leaves a message in a log of some sort.

I may flesh all of that out in a few days and test it. If it works well I'll post the resulting wrapper.

---

### Post by majoridiot on 2009-02-14
> **Cyberai said:**
> I was thinking something like this wrapper would be more reliable as far as knowing if the recording was actually occurring or not:

```


psuedo-code..


mythchanger -g <GUID> -f 6 -v -c <channel>

# Check if the firewire is primed

      test-mpeg2 -r 1 > /tmp/testcap.ts &
       sleep 1
       killall test-mpeg2
       if [ -s /tmp/testcap.ts ] ; then
               echo "#################"
               echo "# Firewire is primed!!!!!!!!!!!!"
               echo "################"
               rm -f /tmp/testcap.ts
       else
               mythprime -v
       fi

```

You could of course, set the entire test under a set of conditions so that it runs until the recording starts properly, or after 5 attempts it fails and leaves a message in a log of some sort.

'zactly...
> **Cyberai said:**
> 
I may flesh all of that out in a few days and test it. If it works well I'll post the resulting wrapper.

if you come up with something that works, posting it might benefit others somewhere down the line, so please do.

---

### Post by Cyberai on 2009-02-14
Well, here is a super crude first swipe written while I was waiting for dinner..

```

#!/bin/bash

rm -f /home/mythtv-user/testcap.ts

CHAN=$1
GUID=$2

mythchanger -g $GUID -f 6 -v -c $CHAN

# Check if the firewire is primed

      test-mpeg2 -r 1 > /home/mythtv-user/testcap.ts &
      sleep 1
      pkill -9  test-mpeg2

       if [ -s /tmp/testcap.ts ] ; 
		then
               	echo "#################"
               	echo "# Firewire is primed"
               	echo "################"
               	rm -f /tmp/testcap.ts
       else
		LIMIT=10
		VAR=0
		until [ ! -s /tmp/testcap.ts ] && (( VAR > LIMIT )) ;
			do
			echo "#################"
               		echo "# Firewire is not primed"
			echo "# Running mythprime"
               		echo "################"		
               		mythprime -v -f 6
			test-mpeg2 -r 1 > /home/mythtv-user/testcap.ts &
      			sleep 1 
      			pkill -9  test-mpeg2
			echo -n "$var "
			(( var++ ))
			done  # 0 1 2 3 4 5 6 7 8 9 10
       fi

rm -f /home/mythtv-user/testcap.ts

```

It doesn't work yet. I don't think test-mpeg2 can differentiate between fw inputs and record the input to disk if you are using more than one STB. Even though all three STB's are primed and respond correctly, test-mpeg2 is producing a zero size file every time.

Anyone think they can clear this up?

---

### Post by majoridiot on 2009-02-14
> **Cyberai said:**
> Well, here is a super crude first swipe written while I was waiting for dinner..

```

#!/bin/bash

rm -f /home/mythtv-user/testcap.ts

CHAN=$1
GUID=$2

mythchanger -g $GUID -f 6 -v -c $CHAN

# Check if the firewire is primed

      test-mpeg2 -r 1 > /home/mythtv-user/testcap.ts &
      sleep 1
      pkill -9  test-mpeg2

       if [ -s /tmp/testcap.ts ] ; 
		then
               	echo "#################"
               	echo "# Firewire is primed"
               	echo "################"
               	rm -f /tmp/testcap.ts
       else
		LIMIT=10
		VAR=0
		until [ ! -s /tmp/testcap.ts ] && (( VAR > LIMIT )) ;
			do
			echo "#################"
               		echo "# Firewire is not primed"
			echo "# Running mythprime"
               		echo "################"		
               		mythprime -v -f 6
			test-mpeg2 -r 1 > /home/mythtv-user/testcap.ts &
      			sleep 1 
      			pkill -9  test-mpeg2
			echo -n "$var "
			(( var++ ))
			done  # 0 1 2 3 4 5 6 7 8 9 10
       fi

rm -f /home/mythtv-user/testcap.ts

```

It doesn't work yet. I don't think test-mpeg2 can differentiate between fw inputs and record the input to disk if you are using more than one STB. Even though all three STB's are primed and respond correctly, test-mpeg2 is producing a zero size file every time.

Anyone think they can clear this up?

if it were me, i would try sleeping at least 5 seconds... it can take a second or more sometimes before the stb
starts sending a stream.

did you test to see if test-mpeg2 works from the command line?

---

### Post by Cyberai on 2009-02-15
Nope. looks like it's a problem with test-mpeg2 on multi stb boxes:

```

mythtv-user@mythtv:~/libiec61883-1.1.0$ test-mpeg2 > /home/mythtv-user/test.ts
Starting to receive
^Cdone.
mythtv-user@mythtv:~/libiec61883-1.1.0$ ls -lh /home/mythtv-user/test.ts 
-rw-r--r-- 1 mythtv-user mythtv-user 0 2009-02-15 10:30 /home/mythtv-user/test.ts
mythtv-user@mythtv:~/libiec61883-1.1.0$ 

```

Any ideas?

---

### Post by majoridiot on 2009-02-15
> **Cyberai said:**
> Nope. looks like it's a problem with test-mpeg2 on multi stb boxes:

```

mythtv-user@mythtv:~/libiec61883-1.1.0$ test-mpeg2 > /home/mythtv-user/test.ts
Starting to receive
^Cdone.
mythtv-user@mythtv:~/libiec61883-1.1.0$ ls -lh /home/mythtv-user/test.ts 
-rw-r--r-- 1 mythtv-user mythtv-user 0 2009-02-15 10:30 /home/mythtv-user/test.ts
mythtv-user@mythtv:~/libiec61883-1.1.0$ 

```

Any ideas?

not sure for a multi-stb setup... you may need to specify a specific node for it to work.  e.g.:

```
$ test-mpeg2 -r n 1 test.ts
```

to receive a stream from the stb on node 1.  to target a specific stb, use plugreport to find out which stb is on which node.

---

### Post by Cyberai on 2009-02-16
Well, took a shot at that last night and here's the result..

```

mythtv-user@mythtv:~/libiec61883-1.1.0$ test-mpeg2 -r n 0 > /home/mythtv-user/test.ts
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
Starting to receive
^Cdone.
mythtv-user@mythtv:~/libiec61883-1.1.0$ ls -lh /home/mythtv-user/test.ts 
-rw-r--r-- 1 mythtv-user mythtv-user 0 2009-02-15 18:04 /home/mythtv-user/test.ts
mythtv-user@mythtv:~/libiec61883-1.1.0$ test-mpeg2 -r n 0 > /home/mythtv-user/test.ts

```

As you can see, no dice. I let it run for about 5 minutes. I'd say something is wrong with my system in particular, but it's a mostly vanilla Intrepid Mythbuntu setup. I've added Boxee and Miro, but nothing else and the repos are standard and untouched since install.

This is very frustreating, I had three out of four recordings fail last night because of firewire connections that weren't streaming properly.

---

### Post by majoridiot on 2009-02-17
> **Cyberai said:**
> Well, took a shot at that last night and here's the result..

```

mythtv-user@mythtv:~/libiec61883-1.1.0$ test-mpeg2 -r n 0 > /home/mythtv-user/test.ts
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
Starting to receive
^Cdone.
mythtv-user@mythtv:~/libiec61883-1.1.0$ ls -lh /home/mythtv-user/test.ts 
-rw-r--r-- 1 mythtv-user mythtv-user 0 2009-02-15 18:04 /home/mythtv-user/test.ts
mythtv-user@mythtv:~/libiec61883-1.1.0$ test-mpeg2 -r n 0 > /home/mythtv-user/test.ts

```

As you can see, no dice. I let it run for about 5 minutes. I'd say something is wrong with my system in particular, but it's a mostly vanilla Intrepid Mythbuntu setup. I've added Boxee and Miro, but nothing else and the repos are standard and untouched since install.

This is very frustreating, I had three out of four recordings fail last night because of firewire connections that weren't streaming properly.

out of curiosity, are you running each stb on it's own firewire port- i.e. 3 firewire cables plugged into 3 diff. ports 
on the computer, or daisy-chained- with one firewire cable running from comp to stb #1 and then cable interconnecting
stb #1-#2 and #2-#3?

---

### Post by lank23 on 2009-05-17
Hello;

I have Verizon Fios with a QIP7100 STB.  The changer works if I use the "-f 6" or "-f 7" option.  But I can not get the "-P" option to work.  As you can see below it reports that it powered the box on but it does not.  Is there anything that I am missing?  Thanks.

```

lank23@ubuntu-desktop:~$ mythchanger -c 504 -f 6 -P -v

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
Powering device on port 0 node 1 succeeded... pausing 5 seconds.
STB Vendor ID: 0x2180 Model ID: 0x8100, (Using user selected channel changer #6)

1 STB(s) found:
-------------
STB 1: port=0, node=1, changer=6, GUID=0x002180fffe4bab21


```

---

### Post by yonkiman on 2009-12-31
> **majoridiot said:**
> source code for mythchanger version .10f beta has been posted at: [https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

Thank you, increasing in-aptly named MajorIdiot.  Mythchanger is a treat!  My HD-PVR and I are very happy now.

---

### Post by majoridiot on 2010-01-01
my apologies to anyone posting, emailing or PMing regarding this, or other mythtv/firewire related utils, that might have gone unanswered...

i no longer have a firewire capable STB and not a lot of free time these days to suss problems with new STBs from long-distance.
(new job and i'm now coding in iPhone app-land)

i'm happy to answer questions and hopefully point people in the right direction when i can, but further code changes or additions from this end are not very likely.

happy new year to the great ubuntu and mythbuntu communities!

---

### Post by AdamWill on 2010-04-17
Just in case anyone's still using this (I've not found a better Motorola changer), I worked out an annoying issue. I wanted to use the -P functionality of the changer script so I could schedule recordings even if the box is powered off, and Myth would power on the box to do the recording.

I found that using the -P option would just stop Myth from working in TV mode at all. Using it from the frontend it'd try and then dump back to the menu immediately after the channel changed.

With some Google help I realized this is due to an unfortunate timeout clash. Myth has a hardcoded timeout: when first launching the TV mode, it'll give up if it takes longer than 7 seconds. mythchanger's -P has a hardcoded 5 second timeout after powering on the box (I assume to ensure it's settled down enough to accept the channel change). With the rest of the overhead in the process, it took mythchanger too long to power on the box and change the channel, and myth would give up waiting for it just a half second or so before it was done.

So I experimented with reducing mythchanger's timeout. You can do this by changing the value on line 510 of mythchanger.c . I've found that 2.5 seconds - value 2500 - works well for my 6200; in tests it seems reliably able to power on the box and change the channel correctly with this time out, and it's fast enough for Myth not to give up on it. Lower timeouts mean it doesn't always change the channel correctly that first time.

So, if you hit the same frustration, try it.

It'd be nice if mythchanger could tell if the box is on and only do the power on operation if it's not, so I didn't need to wait for the 'power on' timeout every time Myth changes channel, but never mind :)

---

### Post by yonkiman on 2010-04-17
> **AdamWill said:**
> So I experimented with reducing mythchanger's timeout. You can do this by changing the value on line 510 of mythchanger.c . I've found that 2.5 seconds - value 2500 - works well for my 6200; in tests it seems reliably able to power on the box and change the channel correctly with this time out, and it's fast enough for Myth not to give up on it. Lower timeouts mean it doesn't always change the channel correctly that first time.

I had the same observation a few months ago and modified the mythchanger code just like you did.  I started with 1 second, then 2..., but if I recall I ended up leaving it at 5 seconds because I still had errors when it was faster.  But I have a Motorola DCH3200 set top box, so that could be the difference.

Thanks for writing this up - I considered my experiment a failure so I didn't; it didn't occur to me that it might still be helpful for people with different model boxes!

---

### Post by bunglebungle on 2010-06-15
I just want to say thanks for this utility.  Myth is supposed to support the DCX3200 but I guess there are a lot of different ids on that STB and it isn't supported out of the box.  I was going to patch Myth itself but I found this and it works just fine with -f 7.  My ids are:
STB Vendor ID: 0x25f1 Model ID: 0xf804

---

### Post by quinnhechtkopf on 2010-08-06
> **Chuffinora said:**
> Is there any reason why this script might not work with a Hauppauge HDPVR?

I am trying to set-up a new MythTV box, with HDPVR and Rogers SA3250 STB.

I followed the HDPVR wiki and with my channel change script set to /bin/true live TV works.

I can run Mythchanger from command line  mythchanger -f2 -c128 tunes my STB to channel 128 etc.

When I try to change channels with myth by using "mythchanger -f2"  in my mythtv-setup channel change configuration, live tv no longer works.

Here is the log output I get:-


2008-12-24 15:16:37.609 Spawning LiveTV Recorder -- begin
2008-12-24 15:16:37.610 TVRec(1): Changing from None to WatchingLiveTV
2008-12-24 15:16:37.613 TVRec(1): HW Tuner: 1->1
2008-12-24 15:16:37.649 Channel(/dev/video0) Error: GetCurrentChannelNum(128): Failed to find Channel
2008-12-24 15:16:37.649 Channel(/dev/video0)::TuneTo(128): Error, failed to find channel.
2008-12-24 15:16:37.649 TVRec(1) Error: Failed to set channel to 2. Reverting to kState_None
2008-12-24 15:16:37.649 TVRec(1): Changing from WatchingLiveTV to None
2008-12-24 15:16:37.650 Spawning LiveTV Recorder -- end
2008-12-24 15:16:37.650 GetEntryAt(-1) failed.
2008-12-24 15:16:37.650 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-12-24 15:16:37.651 TV Error: HandleStateChange(): LiveTV not successfully started
2008-12-24 15:16:37.651 We have a RingBuffer
2008-12-24 15:16:37.651 TV Error: LiveTV not successfully started

Stupid question, but could someone confirm "mythchanger -f2"  without the "" is the correct syntax  (I have tried "mythcahnger",  and "mythchanger -f2 -c" as well but with same results) to use in the channel change script box in mythtv-setup.

Chuffinora's post is very old, but I was having the exact same problem and was able to solve it by running: "sudo chmod +s /usr/bin/mythchanger". This changes user privileges on the mythchanger file to grant temporary root privileges during the execution of mythchanger. Hope this is of help!

Quinn

---

### Post by grygub on 2010-10-25
I am getting 0 ports found. Does this mean that its not detecting my firewire ports? or that no stb firewire ports were found? FYI I have an sa 8300hdc on time warner cable.

grygub@myth-livingroom:/usr/bin$ mythchanger -c 55 -v

mythchanger .10f beta

Acquiring firewire handle... OK.
0 port(s) found
0 STB(s) found:
-------------
Invalid changer option

---

### Post by LowSky on 2010-10-25
> **grygub said:**
> I am getting 0 ports found. Does this mean that its not detecting my firewire ports? or that no stb firewire ports were found? FYI I have an sa 8300hdc on time warner cable.

grygub@myth-livingroom:/usr/bin$ mythchanger -c 55 -v

mythchanger .10f beta

Acquiring firewire handle... OK.
0 port(s) found
0 STB(s) found:
-------------
Invalid changer option




first open a terminal and type ```
plugreport
```

if it shows up then you need to fix your mythchanger code, if not call your cable company and ask them for a working firewire port cablebox

I use ```
mythchanger -f 4 -c *[channel number]*
```

---

### Post by Nausser on 2011-04-21
Please see post number 6 on the following link for current complications with Xfinity upgrade. Same Cisco RNG-150, however, now my firewire control has died.

[http://ubuntuforums.org/showthread.php?t=1693057]("http://ubuntuforums.org/showthread.php?t=1693057")

**UPDATE:**
Please read my latest update on page 3 of the link above. Basically I cannot get mythchanger to function with the Scientific Atlanta Model SA3250HD either.

---

### Post by nojstevens on 2011-09-06
Hello,

I've read this thread several times but don't think my particular issue is mentioned, although a few have had similar issues, their fix does not fix my issues.

I am running Myth 0.24 with a HD PVR. I have a SD8300HD box. I have everything working great with the exception of channel changes. If i use /bin/true in the backend, everything works ok. If I add mythchanger -c or mythchanger -f 4 -c then live tv does not start.

I saw the post above on permissions so I chmod 777 the mythchanger script but still no luck

If I logon via Terminal and type mythchanger -c 1100 then it works fine

Any ideas?

Jon

---

