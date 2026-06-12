---
title: "Maverick Meerkat Sound Problems"
date: 2010-10-29
forum: Multimedia Software
---

### Post by christophevr on 2010-10-29
Hello All,

Many off You does must have noticed : Since maverick a lot of users are left whitout audio or very bad working audio. Most of it is just related to the removal off oss emu into the kernel core.

For no reason some of the makers decided to just remove oss support. This is really stupid . By leaving it there is no any concequence in a good working audio for modern applications and devices.

But now it is removed from kernel Most of HDA audio cards do not run good anymore. Tvtime gnome radio older games all pci tv devices do not work anymore.

They try to let persons use the pulse audio which has some good point's , but is fare very fare from finished. Pulse supports only very few audio cards good. The majority are wronly supported. pci devices are not able any more to interact whit alsa mixer. many very good old applications do not work anymore at all.

Work arounds like sox and so for pulse are very very processor consuming. and will work garbled when performing copy operations or backup operations into background.
On top the sound is always behind the video. This makes watching tv very anoying. rather impossible.

FOR THOSE WHO NEED THE AUDIO DO NOT UPGRADE TO MAVERICK.
IF YOU REALLY NEED MAVERICK, YOU CAN EVENTUALLY INSTALL IT? THEN DOWNLOAD TH LATEST KERNEL SOURCE AND COMPILE YOUR KERNEL SELF WITH OSS INCLUDED.
HOW TO : FOLLOW INSTRUCTIONS ON WEBSITE :

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

Further whe should all togheter ask to the ubuntu's kernel team to reanable oss emu. As it's just a requirement for good working multi media on linux.

Some just asked to remove it actually just one person Mister T chen. This was the worst action ever made by ubuntu. Actually it will cause in time persons who are not able to make own kernel to just leave ubuntu.

All info about this is to find on 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300)

Whe all should join togheter to as the ubuntu kernel teal to enable oss emu again into the maverick kernel core.

This will straight on solve a lot of sound problems which are now rainig down by the bugs launch pad. The majority is just related to the removal off oss emu and the very unfinished pulse audio.

gr christophe

---

### Post by srmcatee on 2010-11-04
Thank you for your post.  I use Mythbuntu and I have fought sound for three days now.  I just do not get it.  Worked fine before.

I hope the folks at Mythbuntu take a serious look at halting or rolling back Mythbuntu 10.  This is really bad karma.

---

### Post by JorritLin on 2010-11-28
Things like these make me contemplate switching to Debian.
I was already blaming some audio program and Wine devs when I saw this, not thinking the unthinkable... OSS might be a troublesome sound layer, but at least give people a choice! 
Ubuntu is by far the most popular distribution for desktops, but throughout the long road between Warthy Warthog and Maverick Meerkat sound regressions have always been there between version upgrades. I would applaud a merger of different sound layers to a result that a mere mortal can understand and control. But first, the alternative has to *WORK* before pushing it to the public. Secondly, this should always be mentioned in the public changelog, so that people can consider the full consequences before upgrading.
Because Ubuntu is the most popular desktop distro out there, people who want to try it will blame this on Linux, not only on Ubuntu. This would give Linux a bad name among private persons who are not familiar with the entire background of this wonderful OS. As such, Ubuntu has a responsibility to be open about these issues and describing them as choices exclusive to Ubuntu and not to Linux as a whole.

---

### Post by rahul.raj on 2010-12-11
B*lls to control freak idiots - if I use an app that is old and no longer under active development, it simply means that I like it and am comfortable with it. Don't give me lectures on "standard user experience" and the need to move forward. F**k you Steve J*bs!! Creating usability issues for people dumb enough to use your products, nice way to treat them!!


.... oh wait! This 'fix' did not come from A$$le, did it!!
Could not notice the difference - please replace Meerkat/Daniel T Chen/Any-other-self-proclaimed-crusader-for-coding-practice-above-"normal"-end-user-comfort for Steve up there.

Time to move on?

---

### Post by JorritLin on 2010-12-11
@rahul.raj:
Constantly swearing and cussing in your post won't help the cause of the poster, nor will it make people take you seriously. Even though you disagree with the decisions made, there are more constructive ways of expressing yourself. Please try to keep things civil here.

---

### Post by likiteasy on 2010-12-12
[FONT=Arial]Hello all , also having problems with audio but besides that,new ubuntu 10.10 like it alot.[/FONT]

---

### Post by rahul.raj on 2010-12-13
@JorritLin:
I fully agree with you regarding the use of cuss words and overt grammatical errors and am sure that it will add nothing to the cause - but frankly with the direction and terse NOs on the 'bugs' forum, I do not have much hope anyway. Plus this sounded so much like the behaviour we have come to expect from the Apple stable that I could not help but troll Apple forums looking for material I could cut-paste here :)
 
(Actually, I was compiling the kernel to enable oss support, and had a lot of time plus frustration due to compile errors. :-( )
 
Please take the message with a pinch of salt!

---

