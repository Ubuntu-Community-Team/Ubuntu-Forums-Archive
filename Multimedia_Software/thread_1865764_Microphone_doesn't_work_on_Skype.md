---
title: "Microphone doesn't work on Skype"
date: 2011-10-20
forum: Multimedia Software
---

### Post by onizuka45 on 2011-10-20
How to get my microphone working on all applications, including Skype? I'm using Kubuntu 11.10 on Acer 3810T. Is there any solution of this?

---

### Post by bilderbuchi on 2011-11-08
that is probably this bug: [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/883404](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/883404)

---

### Post by cespinal on 2011-11-08
the mic volume is down by default in kde for some reason. open up the sound menu (open krunner and type "sound") go to capture devices and crank up the volume....

---

### Post by iamgeniusrnti on 2011-11-11
Hey,

I saw this same problem in another thread and posted below...

I had the same problem on two different  computers (my Kubuntu on a 64 bit PC and my Ubuntu 10.10 running on my  Acer One), both with Pulse Audio.

I spent about a week tweaking on it and I fixed it.  Thru no help of  anyone whatsoever.  While everyone had bright ideas that seemed to work  for them, none worked for me.  Additionally I read a lot about this 'bug' and while I don't disagree this bug exists, it isn't impacting me.

This afternoon, I was poking around the skype forum and someone was  using pavucontrol to adjust his stereo output.  So I did the standard  sudo apt-get install pavucontrol.  Then I gave it a whirl and caught  something evil.

On my Acer One:  If you run pavucontrol and go to input devices, it sees  my microphone as a stereo input.  I noticed when I 'unlinked' the  left/right channels and turned the RIGHT channel all the way DOWN, and  the LEFT channel all the way up, the microphone instantly started  working.  Skype fixed.  

On my Kubuntu PC:  Whenever Skype was up and running, pavucontrol  detected Skype was trying to use the microphone jack for a source and  not my Logitech webcam mic.  So I clicked on the button and changed the  source over to webcam mic.  Problem was instantly fixed.

While the Ubuntu Linux Gods found this problem uninteresting, I hope  this posting will one day help out another of us little people.

---

### Post by bilderbuchi on 2011-11-12
as insane as that solution sounds, splitting the channels and turning right down, left up, as you suggest works for me, too (ubuntu 11.10).

---

### Post by iamgeniusrnti on 2011-11-12
> **bilderbuchi said:**
> as insane as that solution sounds, splitting the channels and turning right down, left up, as you suggest works for me, too (ubuntu 11.10).

Cha-ching!  Karma +1!

---

### Post by yodermk on 2011-11-13
I didn't have to mess with the volume levels like that, but I did solve the same problem using pavucontrol to switch Skype to my USB mic.  I had to do that during a Skype test call.

---

### Post by eric.doe on 2011-11-15
Pavucontrol, splitting left/right channels fixed my internal mic problem.  The only additional adjustment I had to make was disable Skype's ability to adjust mixer levels because it was turning the microphone gain down to 14%

---

### Post by exanime on 2011-12-02
Dude you are a genius!... I had the same issue and some people are saying that it is a kernel problem; however, I noticed that the mic worked ok in Audacity although manual steps needed to be taken to choose the right mic. That led me to believe that it was not a kernel issue in my case at least... 

I then found your post and followed your advice and voila! mic working...

...once seeing it working my wife actually clapped and called me a genius! I selfishly took all the credit hahahaha

---

### Post by iamgeniusrnti on 2011-12-02
> **exanime said:**
> Dude you are a genius!... I had the same issue and some people are saying that it is a kernel problem; however, I noticed that the mic worked ok in Audacity although manual steps needed to be taken to choose the right mic. That led me to believe that it was not a kernel issue in my case at least... 

I then found your post and followed your advice and voila! mic working...

...once seeing it working my wife actually clapped and called me a genius! I selfishly took all the credit hahahaha

Hahahahaha!!!!  Dude that so wrong!!  LMAO!

---

### Post by onizuka45 on 2011-12-03
Will that working on internal microphone? I'm just curious...

---

### Post by Mutikasa on 2012-04-10
Ok I tried this, but when i turned the cam on, microphone stopped again and could not turn it on again

---

### Post by Herpythebrony on 2012-04-10
What type of webcam are you using?

---

### Post by sadcruel on 2012-06-18
> **iamgeniusrnti said:**
> Hey,

I saw this same problem in another thread and posted below...




I had the same problem with "Skype / microphone", in my Acer Aspire 1825PTZ (with Ubuntu and Linux Mint) and your solution worked like a charm.   It seems a common bug in Acer laptops.

Thanks.

---

### Post by nymusicman on 2012-09-13
> **yodermk said:**
> I didn't have to mess with the volume levels like that, but I did solve the same problem using pavucontrol to switch Skype to my USB mic.  I had to do that during a Skype test call.

That totally did the trick. Thanks.

---

### Post by mpc755 on 2012-12-27
The following fixed it for me:


 [https://support.skype.com/en/faq/FA11082/what-should-i-do-if-i-have-a-problem-with-my-audio-quality-in-skype-for-linux](https://support.skype.com/en/faq/FA11082/what-should-i-do-if-i-have-a-problem-with-my-audio-quality-in-skype-for-linux)
[URL="https://support.skype.com/en/faq/FA11082/what-should-i-do-if-i-have-a-problem-with-my-audio-quality-in-skype-for-linux"]
[/URL]
 On Ubuntu, under System Settings - Sounds under the Input tab make sure the input volume of the internal microphone is on

---

### Post by mingiwu on 2013-01-24
I had the same problem and solved by splitting left/right channel. Thank you very much! :D

I found it might be the hardware problem of Acer's laptop.
I use Acer Aspire One and Ubuntu 12.10. I can record two audio clips by using gnome-sound-recorder through internal mic and external mic. But the two audio clips are different. In the clip comes from internal mic, the phase of left/right waveform is inverted ( to simulate stereo sound?) . However the phase of external mic's clip is normal (left/right are the same).

I guess when the Skype captured the mic signal, it just added left and right channel's signal. Therefore, the signal comes from internal mic will become zero, but the signal comes from external mic is loud and clear.

It might explain why splitting left/right channel can work.

---

### Post by travisrichardson1980 on 2013-04-01
[**[COLOR=#000000]iamgeniusrnti[/COLOR]**]("http://ubuntuforums.org/member.php?u=932288&"):

you are awesome! i'm on an acer aspire one running linux mint 9, and had the same problem. followed your fix and it works great now!

thank you so much for your contribution! my friends can hear my voice now! :)

"On my Acer One:  If you run pavucontrol and go to input devices, it sees   my microphone as a stereo input.  I noticed when I 'unlinked' the   left/right channels and turned the RIGHT channel all the way DOWN, and   the LEFT channel all the way up, the microphone instantly started   working.  Skype fixed." -iamgeniusrnti

---

