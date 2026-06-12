---
title: "skype trouble"
date: 2010-10-04
forum: Multimedia Software
---

### Post by andypearce on 2010-10-04
Hi all I have re posted this thread I started called 'problems with Skype' that I posted several days ago in General Help but I realise in the wrong place/category to get help from those with a particular interest in this area of the 'workings' Sorry to all.
Here it is:
**Problems with skype**
Hi all, I am using a Toshiba satellite pro L100 with Ubuntu 10.4. I have installed Skype from the list from Ubuntu software centre. I am using a Logitech c200 webcam with its own mic.

I have managed to 'install' the webcam and have got it working on cheese and managed to get the webcam working on a test call with skype. To make the mic work I went to sound preferences..then input.. then selected '802 analog mono' which then registers sound on the scale above to show it is working. All well and good.

I have then made a Skype video call to my friend. All works well-ish. She can see me and I can see her. My own image is jerky (not personally... the way the video moves!:)) but during the conversation I was having she stopped being able to hear me, after 5 minutes or so, she could hear electric bleeping noises, but she could see me. The same thing happened with my first test call to my mom and she lost my sound as well. At the same time my mouse stopped working and I had to resort to the touch pad which did work.

I have looked through many posts, instructions, and googled the problem and have become quite confused by problems, solutions and language. The jerky video image I had thought was probably for the same reason that flash players and iplayers cannot play full screen on this laptop... it is probably not 'big' enough (????) to process all the info... works fine on tiny screen.That is OK... I have spent hours on it,downloaded medibuntu etc and have given up and come to that conclusion.

The sound/mouse is a big problem... can anyone out there help,or point me in the right direction. 
Thanks
Andy

PS Some people are reporting Skype crashing.... is my sound problem a symptom of Skype 'crashing'? Some people are inferring Skype does not work very well on Ubuntu... is this right? A

---

### Post by Claus7 on 2010-10-04
Hello,

just try to use this command when you are launching skype:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and yes, since skype is beta for a long time, that means that there are some things remained to be fixed.

Regards!

---

### Post by andypearce on 2010-10-05
Thanks claus7 for your response. Where would I put that command... I go to applications and choose skype, put my password in and off I go (or not!:(). Do you mean open the terminal and copy it in to there, would I have to do it more than once?
Thanks
Andy

---

### Post by Claus7 on 2010-10-05
Hello,

take a look at this:
[http://ubuntuforums.org/showthread.php?t=1145175&highlight=skype](http://ubuntuforums.org/showthread.php?t=1145175&highlight=skype)
among other things that you can try.

Just opening a terminal and trying this out, you could check easily if this is a solution for you. Then you could make it permanent with different ways.

You are welcome and hope this helps,
Regards!

---

### Post by andypearce on 2010-10-06
Thanks I will give it a go and have had a look at the other thread....lots to learn but will get through it, thanks again.
A

---

### Post by andypearce on 2010-12-26
I have had a good go with skype. Using the LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype pasted into a terminal gives me skype two way video without sound being received by the person I call... well I am told there is some electronic type of noise that comes out for a bit then nothing then my  mouse stops working. I can see and hear them perfectly. If I go into skype from my icon in applications, as I used to, and if I adjust the settings in sound to and external mic I get sound recieved by people I call but no Video...again I am receiving them perfectly then after a couple of minutes this fails and my mouse stops working....Anyone any further suggestions?
Thanks 
Andy

---

### Post by andypearce on 2010-12-27
Bump:)

---

### Post by andypearce on 2010-12-27
Ok an update. I have had it with skype for a bit... it is taxing me beyond the limit of my patience. So since bumping the post I have looked for an alternative. Ekiga.....
So I have set it up... got an address... with my logitech webcam plugged in done the settings as logic would dictate. Selected sound preferences, input, selected the external mic... tested it by speaking and watching the sound bar go up and down.. then performed an echo test. I can see me albeit highly pixelated in the little screen but instead of my voice coming out there is a horrible noise... it seems to match my voice in intensity and duration of words. I have even turned down the input in case too much sound was going in and upsetting the mic but it was the same..I know this mic works...I had a conversation using it last night.... I know the webcam works as I could see myself during a skype call when the horrible noise was coming out at the other end...or not when nothing comes out at the other end. I can see and hear my friends perfectly... they are sending fine. The video and sound does not want to work at the same time.... unless in a skype test call, or if it does it stops one way or the other pretty quick.
It this a codec problem?
I can not think it is the webcams problem.
It has to be how my laptop reacts to the software.. skype and ekiga..and most irritating of all is I have very sweaty fingers and it constantly crashes my mouse which means I have to use that little screeny thing that does not like sweaty fingers at all!!
As usual,all help would be gratefully received, and I know it helps others in a similar situation... if I can ask the right questions. I am a beginner really even though I have been at this Ubuntu business a while and fixed lots of problems with help from lots of people on the forum. I am thinking this one might be beyond me....

---

### Post by TopEnder on 2010-12-27
andy, The following link may be of help to you "Skype Sound and Audio Set-Up" also their Forums and Help & FAQs maybe of help also. TopEnder

[http://www.skype.com/intl/en/support/user-guides/sound-setup-linux/](http://www.skype.com/intl/en/support/user-guides/sound-setup-linux/)

---

### Post by andypearce on 2010-12-28
Thanks TopEnder... I will have another go with it and see what I can do. I have had a look on the skype pages before but think you are right to be directing me in that way again. I don't think ubuntu is the problem (at this stage!)  
I will post my results for others.
Bye all for now.
A

---

