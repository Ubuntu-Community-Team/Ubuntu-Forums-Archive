---
title: "Ubuntu with no sound at all"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by UpMarc on 2007-01-03
I'm brand new to Linux/Ubuntu environment, which I have installed (6.06) last June as a 2nd OS in addition to the existing Windows. Recently I updated it to 6.10. All had been working reazonably despite of a sound conflict betwenn multimedia apps and a game site ([www.pogo.com):](www.pogo.com):) starting one made the othe mute.

Three days ago, I was at the game site and Ubuntu froze completely and I had to restart with the boot button of the PC. Coming back, I realized that I had completely lost the sound in Ubuntu, as I am up to now. Nevertheless, sound is still working normally in Windows environment. 

Due to my inexperience on Linux/Ubuntu and lack of knowledge of commands for this OS, I got some help from folks in IRC ubuntu-br. We are making several tests since then. The last ones were tries to get sound using both Live CD's (6.06 and 6.10), but it didn't work. But I insist that sound works in Windows.

Thus, by suggestion of the ubuntu-br folks, I'm asking for help here, but need your comprehension for my small technical knowledge, for which I thank in advance.

---

### Post by haiku99 on 2007-01-03
check out this guide, it should help to identify the problem:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem)

---

### Post by sgx on 2007-01-04
Save your sanity, and reinstall fresh, do not update. Audio is too flawed and complex to waste
time on, when this kind of nonsense happens, (alsa devs agree) and if sound is still gone after fresh install, frisbee toss that soundcard, or if its onboard sound, get a good soundcard and disable that feeble wretch!
 I had a 24 bit Envy based 7.1 surround card that sounded fabulous, $23,
now have mAudio 24/96...fabulous in all aspects +i/o, $99 max...If you need full Distro to avoid
update, but you're on dialup, someone at a library or school should have broadband, or get
a magazine with cover dvd...please don't fight the dead! Hope this helps!

---

### Post by UpMarc on 2007-01-05
Haiky99,

      Thank you for the interest. I have gone to the site you indicated, but this just confirmed what I said in my first post: it's useless to take me to technical instructions; I don't understand them. They say about commands etc, which is "greek" for me. I'd have to take a whole course just to be able to understand it. I need objective help.
      Again, thank you anyway.

UpMarc

--------------------------

Sgx,

      I also thank your very reasonable suggestion; I'm sure it'll work. But must tell you that, when I choosed Linux / Ubuntu to be my second and main OS it was due to its philosophy, human kind constructing to human kind (freely). So, we shall all work on its improvement.
      If I simply change my soundcard, what I'll be doing is what we call here in my country as "to cover the sun with a sieve", i.e., I won't solve a problem, but hide it. In our case, I think we should try to identify the problem so that it won't happen again - to anyone.
      So, I'd like to come back to the real problem and remember that:
- the sound works normally in Windows OS;
- the folks of IRC ubuntu-br and I have made several tests and it didn't work;
- the "Live cd's", both 6.06 and 6.10, didn't produce no sound at all, as we hoped;
- in principle, the live cd's shoudn't read pre-existing OS, but I'm afraid they are, otherwise they'd produce sound;
- with live cd's sounds should be produced and tested through "Preferences>Sound", and nothing happens.
      Thus, I'm still waiting for technical support and help from people who knows deeply the Linux/Ubuntu OS.
      Again, thank you.

UpMarc

---

### Post by sgx on 2007-01-06
Hi...
with all due respect, most people forget linux is backwards to windows.
In windows, you buy the software for your hardware. In linux, you buy your hardware for your software. If you fail to put this simple and
inexpensive algorythm into practice, you will be one of the thousands
wasting their life, creative energy, and sanity in a never ending littany
of forum posts, saying, 'my hardware does not work, linux is crummy'
...or 'my hardware is crummy, because it won't work with linux', when
the truth is that you must by your computer equipment with the same
intelligence you use when buying food or cars or clothes...if the shoes hurt your feet, the food makes you fat, and the car breaks down on the way  to the doctor, then welcome to linux...but wait!!! You say your
shoes fit, you're healthy, and drive a Mercedes...Thats because you are smart. If everyone applied -those- smarts to the center of their information/media center, they would quickly learn that 'linux hardware'
=meaning hardware that 'just works' ...it is easy to find on google, cheap to
buy in stores, and allows  you to use your computer to do more than
just figure out how to use your computer. The problem is people get all
independant and philosophical, or join camps and crusades, and miss
out on the opportunities for the small and daily victories that happen when you simply have the right stuff. Buy a soundcard. Make wonderful music. You won't ever look back!

---

### Post by johnpipe on 2007-01-06
One of  the things that new linux users are not always aware of is that sound card support in linux, as hardware support in general, comes mainly from volunteers in the linux community who reverse-engineer the necessary drivers for our hardware.  Sound card support from the manufacturers is only just beginning; the more people who start using linux, the more manufacturers will "get on the bandwagon". 

 In the meantime, some cards may just not be easy for volunteers to figure out how to get working, so in such a case the only recourse may be to replace it.

In order to even try to find a solution to getting such cards working, it is necessary to either learn how to do simple technical commands that will provide information about your soundcard, or get help from your local user group to help you get the information, then post the information to the Ubuntu forums. 

Microsoft does not provide information to linux on how to get sound working, nor does it share it's drivers.

HTH, Johnpipe

---

