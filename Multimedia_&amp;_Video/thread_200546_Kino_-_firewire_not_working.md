---
title: "Kino - firewire not working"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by Blind-Summit on 2006-06-20
I have an ASUS A7N8X mobo and I have 2 firewire ports that are connected from some pin headers from the board. Worked fine 100% of the time in windows.

I'm trying to capture some video from my Sony HDC-24E camera but it's not doing much.

I followed some guides about adding raw1394 and video1304 to my /etc/modules file but still nothing. It doesn't see the camera is connected, and all the capture buttons are greyed out

Why is everything so hard to setup. Bloody microsoft with it's oversized marketshare and substandard software. I wish manufacturers would release more linux drivers and code :(

---

### Post by Svictor on 2006-06-20
I'm not quite sure you're talking about a driver problem.

Do you have write access to /dev/raw1394 ? Try ```
ls -l /dev/raw1394
```  If it belongs to user "root" and group "disk", you probably don't. In this case:
```
sudo chmod 777 /dev/raw1394
``` or even
```
sudo chown name-of-your-user /dev/raw1394
``` Then check to see if kino still doesn't recognize your camera.
Caution however: this might imply a security risk (see this discussion: [https://launchpad.net/distros/ubuntu/+source/kino/+bug/6290)]("https://launchpad.net/distros/ubuntu/+source/kino/+bug/6290")

As an alternative to kino, you can try dvgrab (from the repos): a simple commandline video grabber.


Good luck!

---

### Post by Blind-Summit on 2006-06-20
Great stuff - thanks :)

The thing about drivers was just me venting my frustration! I have a decent photo printer (Epson R300) but if I want to use any of the settings or the print onto printable CD / DVD - then I have to use windows. I also have a Sony W100 8.1MP camera and I can't connect that to get my photos off via USB.

I'll raise these in other topics in the right sections.

Thanks Svictor for helping me out :) Any ideas for a good editing suite for videos? Kino looks a bit basic

---

### Post by Svictor on 2006-06-20
I guess you could try [Cinelerra]("http://heroinewarrior.com/cinelerra.php3") (you'll probably find it in the repos as well). However, I found it too sophisticated for me. For basic editing, kino+plugins works quite fine.

---

### Post by Blind-Summit on 2006-06-20
Where did you get the plugins from?

I have been using Vegas Video 6 under XP and I get used to higher end software pretty fast. That Cinelerra looks just perfect for me - thanks again :D

One final question - rpm files? I'm terrible about building any code and have been used to getting things from the packet manager or at best - downloading and installing from a deb file.

How and what do I do with the rpm?

Thanks

---

### Post by Blind-Summit on 2006-06-20
No matter. I used alien to create a deb file and installed that. It still looks a bit basic to me - but I guess it will do. Thanks :)

---

### Post by Blind-Summit on 2006-06-24
[QUOTE=Svictor]I guess you could try [Cinelerra]("http://heroinewarrior.com/cinelerra.php3") (you'll probably find it in the repos as well). However, I found it too sophisticated for me. For basic editing, kino+plugins works quite fine.[/QUOTE]



OK, I gave it a go and it's terrible. I can't get audio or video to work on it at all. Kino plays back my dv file with an image and sound (although a bit crappy looking) but it works. The editing for kino is so very lame. The Cinelerra is pretty terrible.

Does linux not have a decent video editing package?

---

### Post by Svictor on 2006-06-24
I'm not sure. Maybe if you gave details about what "decent" means to you, and what you try to do, people might be able to help you in a more accurate way.

---

### Post by Blind-Summit on 2006-06-26
Cinelerra just looks terrible and seems quite basic. This is a shot of Sony Vegas 6 which I used under windows. Whilst I really don't expect a 1:1 copy, I just thought there would be a parallel. Vegas is a lower level app compared to say Adobe Premier Pro.

[IMG]http://www.manifest-tech.com/images/pc_video/sony_vegas6/v6-hdv.jpg[/IMG]

I just want something that's easy to use (that also actually works! - see last posts) and will allow me to edit a professional looking video and render it afterwards.

---

### Post by mediaservant on 2006-06-29
I went through the same thing myself a few months ago.  I wasn't 100% legit on any of my software and wanted to be.  I went with ubuntu, and endured much pain and many late nights getting my system "just like it was with windows".  That means dual screens, firewire, video editing, graphics, sound, all of it.  I did all that.  

I captured video via kino and edited it in cinelerra.  

Cinelerra is "powerful" which people will say.  Powerful like strapping a corvette motor to a lawn mower.  It might get you down the block, but I wouldn't want to drive it to work everyday.  (Editing in kino is, to me, a mystery - I couldn't figure it out.)

Basically it was the most painful editing experience I ever had.  I use vegas video, I have since 3.0.  I had trouble importing the video kino got for me.  I got the hang of editing in cinelerra, mostly, eventually, but it was painstaking and tedious.  I had trouble rendering it.  Then, I had to render to AVI and convert it to mpeg VIA COMMAND LINE!  Come on, people.  I'm a geek, but I wouldn't brag about having to do it that way.  

I got the job done though.  One huge problem in cinelerra is putting text onto the screen.  It does credits, but even after extensive digging into the docs there is no "text tool".

I found main concept "mainactor" which is a commercial open source video editing package.  Aha, I said.  It works with windows, linux, etc etc.  I tried it.  It is nice.  Check it out.  It's the same people as the mainactor mpeg codecs.

It comes in a RPM or a deb.  The RPM was stable in ubuntu using the "alien" command.  But some menus were just plain missing.  The .deb, which SHOULD work fine in Ubuntu, had all the menus but was unstable.  If it was stable, I would have paid MONEY for it and still be using ubuntu to this day.  Maybe there is a recompile one could do for ubuntu.  

So after about a month of pain, and my wife putting up with the late nights with this "linux" mistress, she quietly approached me and said it wasn't working.  

I agreed, and went onto newegg.com and ordered windows xp, vegas 6.0 (with dvd) some ram, a new hard drive, and now I am happily using all legit software and it "just works".

Now, if someone would come on here and say "do this, do that and then this, and you can use vegas 6.0 seamlessly and 100% foolproof on linux, well, I'd think about dapper.  I haven't heard that vegas works on wine yet.

Linux __is there__, I tell you.  You can do _ALL_ the same things as windows*.  Eye candy interface.  Codecs.  Web.  Firewire.  Sound.  TONS AND TONS of free, powerful software.  USB flash drives, plug 'em in.  ubuntu rocks, seriously.  I really like it and I miss it.  I grabbed the system sounds and put them into windows XP, I liked it so much.  So don't think I'm bashing anything.

But right now there isn't any video editing software that is on par with vegas video or it's peers.  Video editing is now my business.  I can't play around, and for goodness sakes, I can't use cinelerra!

Cameron

*almost all

---

### Post by gratefulfrog on 2006-06-29
cinelerra requires some patience but works very well, also requires some learning, take a look at my set up page at:

[http://gratefulfrog.net/]("http://gratefulfrog.net/")

If that's not enough, try the IRC #cinelerra on freenode for more extensive help,  also I give some links on that page, too.

It's possible to do high level video editing on linux, but requires some patience, and quite some knowledge - if you're looking for something that's point and shoot, then you probably won't be happy with linux video editing...

be sure your *1394 devices are +r+w for all users and you should be able to capture dv; capture works perfectly with dvgrab (command line version of kino).

let me know if you need more help!

Cheers,
GF

---

### Post by Blind-Summit on 2006-07-03
See, this is the problem. Although windows is terrible blah blah and all the other bashing - we have to be honest here. I as a user, jsut want to get stuff done. That's why I turn my PC on. I want to load a program and do what I want. 

Like mediaservant said - Ubuntu just doesn't have the software like Vegas. I also used Vegas 3, 4 and 6 on windows and it was perfect for what I needed. It worked straight away, I didn't need any command line knowledge or to read ANYTHING about it to make it work. I didn't need to setup any hardware - it all worked out of the box.

Whilst I would love to learn all the commands and the ins and outs of Linux and the associated packages - that's just not what I want to do. It's been a non-stop struggle to get multimedia to work, and video / audio editing is just way way way off the mark.

I'm sorry as I really wanted to be happy with ubuntu.

I will give that mainactor a go

---

### Post by stani on 2006-07-13
Hi,
I try to use firewire through a pcmcia card, which has two firewire ports and two USB ports. My laptop ibmx30 has also a built-in firewire port and that works fine. As a test I want to use dvgrab. I've done this but it fails:
```
$ sudo chmod 777 /etc/pcmcia/ieee1394
$ sudo chmod 777 /etc/pcmcia/ieee1394.opts
$ dvgrab --dv1394 /etc/pcmcia/ieee1394
raw1394 - failed to get handle: Permission denied.
$ dvgrab --dv1394 /etc/pcmcia/ieee1394.opts
raw1394 - failed to get handle: Permission denied.
```

Anyone can help?

Thanks,

Stani

---

### Post by jrickard on 2006-11-30
Unfortunately all you say is true.  I've been playing with Fedora Core 4/5/6 and now Ubuntu 6.06 and 6.10.  If you complain about something not working, teh group generally attacks like a pool of sharks that you are an idiot and aren't asking the correct questions.  It is mind boggling.

Linux is a cultural backwater much akin to Northern Arkansas.  It IS actually 
quite a bit of fun if you like mastering totally arcane information in order to be able to service the machine, ala personal computers in the early 1980s.  
And I'm a sport.  Right now I'm reading an entire book devoted to the use of "Regular Expressions."  I'm utterly fascinated that they still use this stuff and in fact revel in how much power they can cram into the least readable line of special purpose characters.

If you actually need to use a PC to do something, I'm afraid we are quite stuck with Microsoft and the industry specific programs like Adobe Photoshop, if you are dealing with photographic images or Autocad if design, or Quark Express for publishing, and probably Adobe Premier or Vega 
for video editing.

Linux brings back the toys and the joy of dealing with computers as toys just as an end to itself.  But if you lean on it to actually do some work, it breaks into sixty tiny pieces at the slightest touch. And you spend the rest of your life combing forums and books for some magic snippet of code to glue it all back to together again.

Jack Rickard

---

### Post by Dragonbite on 2006-12-05
> **Svictor said:**
> ```
sudo chmod 777 /dev/raw1394
```Then check to see if kino still doesn't recognize your camera.

I did this and got access to the camera via Kino, but the changes were lost when I rebooted the system, how do I make it permanent?

A Kino-speicific question: I am seeing the video in slow-motion and the sound is close to the range only dogs can hear!  I theorize if I can get the frame capture up-to-speed it may fix the sound problem, any suggestions? Is there a configuration I should change in the Capture Preferences?

---

