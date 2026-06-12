---
title: "After Installing the recommended packages, Quicktime still wont play"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by Jbanicar on 2007-10-23
How do I get Quicktime trailers to play? I downloaded the package from ubuntu-restricted-extras, and I already have the libdvd... and when I go to view one, it wont work.  What do I need to do?

---

### Post by SunnyRabbiera on 2007-10-23
did you download mplayer?

---

### Post by Jbanicar on 2007-10-23
Yes

---

### Post by SunnyRabbiera on 2007-10-23
did you try to download the totem plugin for mozilla?
or the mplayer one?
did you try the win32 codecs as well?

---

### Post by Jbanicar on 2007-10-23
Where do I get the pluggins?  How do I know if I have them?  I right click on the Quicktime trailer, and it only gives me the option of playing it with Totem, which says that it is unable to when I attempt it.

---

### Post by SunnyRabbiera on 2007-10-23
well could you tell me how you installed what you have so far?
did you use synaptic or did you use the add/ remove applet?

---

### Post by Jbanicar on 2007-10-23
I think I just did Add/Remove.  For some of the other stuff I did the sympactic or whatever it is called.... I cant remember how I did everything, because I've been jumping through hoops trying to get things that should just work already.

---

### Post by SunnyRabbiera on 2007-10-23
well sorry but the thing to remember is that Ubuntu and windows (assuming you are coming from windows) are two different operating systems hand have two different goals.
The reason for ubuntu not shipping things like quicktime stuff by default is because of legal issues surrounding it on linux... this is no fault of linux and is more of the fault of companies like microsoft apple who are greedy on what they give up.
Now luckily for you there are tools to get linux media ready, and synaptic is one of them.
but you might want to look up other ways to download proprietary codecs such as automatix...
if you need help on how to install these things, just ask... we dont bite unless you want us to ;)

---

### Post by Jbanicar on 2007-10-23
So what codes should I download and what should I use to get them?

---

### Post by SunnyRabbiera on 2007-10-23
well the win32codecs are a good place to start, so are the gstreamer ones too.
but the win32codecs might work better for you but they are not in the repositories by default.
what you might need to do is to get automatix, its pretty fair at what it does...
I know its annoying to remember so many things but this is mainly due to legal issues rather by any fault of linux...

you might want to post some of your computer information for us to further help you, do you know what kind of processor you have?
this sort of thing matters as certain apps and codecs are not made for say AMD 64 computers.

---

### Post by Jbanicar on 2007-10-23
I tried putting in "automatix" in the synaptic and nothing came up.

My system is a Dell XPS Gen_2  (2.0 Ghz Processor / 2 GB RAM / Geforce 6800 Ultra Go).

---

### Post by SunnyRabbiera on 2007-10-23
automatix is not in the synaptic repositories, you can get it here:
[automatix]("http://www.getautomatix.com/")

sorry about the confusion :popcorn:

---

### Post by Jbanicar on 2007-10-23
Thanks!  That auto program did the trick for getting that MPlayer plugin installed, and I was able to play the movie trailer over on the quicktime site successfully.

Problem solved!

------------------------

Follow-up question, how do I get the YouTube audio to play through my USB Headset?  It works perfectly with: Skype, VLC, Pidgin, etc.  It is recognized by Ubuntu perefctly, and I have verified this by doing the terminal option of seeing what it recognizes.

But whenver I go to play a YouTube video, it just plays straight through my laptop speakers instead, and even if I right click on it, only the Adobe Flash options come up, which I see nothing about selecting my USB Headset since it is flash.

Any ideas?

---

### Post by SunnyRabbiera on 2007-10-23
hmm you might have more issues with that one as it might not work with usb headphones...
was that an option when you used windows?

also I am glad automatix worked for you, it takes time and patience but you might be able to make ubuntu work in a roundabout same way as windows in some areas... but that usb headphone issue might be out of our hands.

how did you learn about ubuntu might I ask?

---

### Post by Jbanicar on 2007-10-23
I first used tried Ubuntu on a computer at work on campus last semester (Spring 07), when I was working with the Global Classroom, and when I was messing with it, it was already on there when I started.  I had never used Linux before, but being a computer person, I always read about it, so I knew about Linux in theory but never had the chance to mess with it.

Well, it was really cool and different... so I wanted to just try all kinds of Linux, but mostly, I stuck with Ubuntu because it was the easiest and I liked the look of it, as most other distros were pretty bland, it had one of the easier methods of finding programs and installing them.  Plus, even before that, I had always been using Firefox instead of IE, becaue you could custumize it, and it was more secure (not to mention faster to me it seemed).

Anyway, I had tried a Live-CD then, and things just didnt work quite right on my laptop, and I didnt know anything about partitioning or whatnot, so that's about as far as I could do at the time using it on a day to day basis.  That summer I went to Australia and read a Linux Magazine in a bookstore that talked about all these cool effects, and how Linux was basicly a free-Vista effects version that could do all the normal stuff fine (except known for gaming oriented things, although I know about Cadeda spelling?).

Anyway when I read that Ubuntu was coming out with a new verison soon (in the next two weeks is when I read back up on it), I got really excited, because I knew that if I was going to try it out seriously... that my best shot would be with Ubuntu, because of its stability.  And then I saw the article about how Dell was supporting it in some small way with computer orders, and since I have a Dell, it seemed like the best option.  

Mysteriously enough, I tried to do a Mandriva2008 partition a week before Ubuntu, because it had the Compiz and everything packaged together (and was out)... but the partition never set up the dual-boot correclty, and I was unable to access it... I tried on their forums, but I got no-help responses AT ALL... so I just waited for Ubuntu7.10  

Well, it came out, and I tried the Live-CD and everything seemed to work fine.  It saw my Nvidia card and said that it had drivers for me; this was a HUGE plus, because I need things to work good from the start.  So after reading and reading, I figured out how to do the partition correctly, and wham! installed fine, dual booted, and it wasn't too long before COmpiz-Fusion was working ok, and I began the long and interesting process of finding out about which codes I needed, how to install various things, use the Terminal more, and setup Pidgin (IRC channel is a life saver for help).

All in all... the only thing that I can't get to work right now is my printer (one of the Ubuntu goals for this 7.10), which even though it is recognized ( HP Deskjet D2300 ), I cant get it to print a PDF.  

Also another downside, is that me and my fiancee rely on communication via Skype, and there is currently no video option on the Linux skype, which means that I have to boot back into Windows every time we communicate.

That's my story and I read yours btw.


P.S.
I found out my print problem.... the USB cable wasn't plugged in! LOL... I r dupit... I got the one that was, confused...

---

### Post by SunnyRabbiera on 2007-10-23
hehe, well glad thats working too...
the skype issue might be your biggest issue though as skype hates us...

---

