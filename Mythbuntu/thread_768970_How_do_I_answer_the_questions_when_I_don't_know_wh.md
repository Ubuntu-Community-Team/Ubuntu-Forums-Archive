---
title: "How do I answer the questions when I don't know what they are talking about?  :)"
date: 2008-04-26
forum: Mythbuntu
---

### Post by thafemann on 2008-04-26
Hey there,

I am really, really new to this myth-tv thing.  I got excited when I saw it at a conference.  I purchased a Hauppauge PVR-500 kit with  the remote and all.  

Okay, it is not as easy as plugging in the 8.04 cd and just BOOM I thought it would work.  Well, what I realized that I just don't understand what I am trying to do.

When I ran through the setup, it asked me all sorts of questions.  I don't know some of the questions that they were asking let alone what the answers should be.

I am in Time Warner country with a Pioneer tuner model BD-V1000.  I don't have a clue.  I thought I could just plug in the cable from the wall, bypass the tuner, and at least get some stations.  When I press, "Watch TV" the monitor goes black for a while and then comes back.

Okay, I am an idiot.  I need to read up on what I have, what I am trying to do, and begin to understand this TV lingo.  Can someone point me to a book or readme?  Does anyone have the answers to questions on what type of signal I should be getting?

TIA

Tom

---

### Post by Trimble Epic on 2008-04-26
Hi!  Welcome to the club, welcome to the community :)

Ok, so you're really starting with just a box of equipment.  You have your Hauppauge kit, and I assume the basics (cpu, HD, video card(hopefully with TV output)), and I assume a copy of the 8.04 Mythbuntu CD.

For the most part, the installer's defaults are good enough to get you started.  At least, if nothing else, they are good enough to get you through the installer.  You should consider just running through it, scribbling down notes of what you don't understand and what the options are so that you can come back here and ask us questions.  Unlike MANY other Linux communities, the Ubuntu community actually seems less stuck-up than the rest, which is why I chose Mythbuntu.

Most of us, on our first Myth box, have run through the setup, experimented, blown it all away and reinstalled over... and over and over.  Don't be afraid to run through the setup and just make your best guess.  The worst that would happen is starting over.  You learn ALOT about Linux just doing it over and over, and asking questions.

Good luck!

---

### Post by thafemann on 2008-04-26
Oh nuts.  I just checked  I have a WinTV-PVR 500 Windows Media Center Edition Kit.  Okay, I suppose that means that the "kit" portion should not work, but what about the card.  You know, I assumed that CDWG would have known better when I told them that I was putting together a mythtv box using linux and mythbuntu.  This is what you need, was the response.  Bummer

---

### Post by .nedberg on 2008-04-26
I have that kit too. it works just fine. Have not tried the IR-blaster as I don't need it, but it should work.

I also reinstalled myth a lot of times before I finally got it. Mythbuntu makes it a lot easier that anything else I tried (KnoppMyth and Ubuntu + Myth packages). Hang in there! Myth is GREAT when you get it going.

Try to ask specific questions and you will get answers here at ubuntuforums!

---

### Post by thafemann on 2008-04-26
Okay, here is a direct question.  How do I plug in the cable?  Sound kinda stupid, I know.  Do I plug in the cable to the computer right out of the wall, or do I plug it in after the cable box?  
I have a tv in another room plugged directly into the wall cable, and all I get is the first 100 or so channels.  The cable box (pioneer) gives me all of the 1000 number channels.

Tom

---

### Post by thafemann on 2008-04-26
A few more questions, while I am plugged into the wall with the cable, when it searches for channels it finds none.

Where do I find and set the IP address of the computer

---

### Post by .nedberg on 2008-04-26
> **thafemann said:**
> Okay, here is a direct question.  How do I plug in the cable?  Sound kinda stupid, I know.  Do I plug in the cable to the computer right out of the wall, or do I plug it in after the cable box?  
I have a tv in another room plugged directly into the wall cable, and all I get is the first 100 or so channels.  The cable box (pioneer) gives me all of the 1000 number channels.

Tom

If you want all the channels, then into the cable box. But you will need to get the IR-blaster to work if you want to change channel from Myth. I plug it into the wall.

You can find the IP of the computer with```
ifconfig
```it will be on the form 192.168.x.x (probably).

When you search with mythtv-setup it should find all the channels. If not, you could open up a terminal and execut 'mplayer /dev/video0'. In an other terminal play with ivtv-tune to change channel. Have a look here: [http://ivtvdriver.org/index.php/Ivtv-tune](http://ivtvdriver.org/index.php/Ivtv-tune)

ivtv-tune is part of ivtv-utils, I used it under KnoppMyth with the same card.

---

### Post by thafemann on 2008-04-26
Which search version do I use?  I used Try-all to see if it would find any.  I also tried "cable" "cable-hvc" "cable-irc".
I see things and they are show up, but when I go to "watch live tv" it goes black and then comes back to the main screen.  Is there something I need to do to watch it?  What viewer do I use to watch tv on a remote computer?
Tom

---

### Post by thafemann on 2008-04-26
Which search version do I use?  I used Try-all to see if it would find any.  I also tried "cable" "cable-hvc" "cable-irc".
I see things and they are show up, but when I go to "watch live tv" it goes black and then comes back to the main screen.  Is there something I need to do to watch it?  What viewer do I use to watch tv on a remote computer?
Tom

---

### Post by thafemann on 2008-04-26
Which search version do I use?  I used Try-all to see if it would find any.  I also tried "cable" "cable-hvc" "cable-irc".
I see things and they are show up, but when I go to "watch live tv" it goes black and then comes back to the main screen.  Is there something I need to do to watch it?  What viewer do I use to watch tv on a remote computer?
Tom

---

### Post by .nedberg on 2008-04-26
Did you add the channels in Channel editor? Did you add the card and input devices?

I am going to bed now, and I will be away most of tomorrow. Have a look in the mythbuntu manual ([http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf)) if you did not already read it.

You would use a mythfrontend to watch tv on a remote machine. I found it easier to set up a box with both back- and frontend first, then connect a remote frontend.

---

### Post by thafemann on 2008-04-26
Which search version do I use?  I used Try-all to see if it would find any.  I also tried "cable" "cable-hvc" "cable-irc".
I see things and they are show up, but when I go to "watch live tv" it goes black and then comes back to the main screen.  Is there something I need to do to watch it?  What viewer do I use to watch tv on a remote computer?
Tom

---

### Post by superm1 on 2008-04-26
If there is some confusion in the installer itself (the Ubiquity part), please file some bugs to clarify what you don't understand.  That part is supposed to be very straightforward.

The MythTV part however, I can tell you there are usability issues that need to be addressed, but that's something to deal with upstream about...

---

### Post by murchball on 2008-04-29
I bought the Practical MythTV book (ISBN-10: 1590597796) which I found helpful on a lot of these basic concepts. It was written for 6.06 and .20 but most of it is still relevant. The other thing that I found useful for determining if your tuner is working properly is tvtime. Just install it from the repos (sudo apt-get install tvtime) and run it. It's a very simple app that just allows you to watch tv, no pvr functions. If tvtime doesn't give you any video, your card is probably either not connected properly or is broken. EDIT: it turns out that tvtime will not work with a Hauppauge x50 or 500, see Superm1's post

---

### Post by superm1 on 2008-04-29
> **murchball said:**
> I bought the Practical MythTV book (ISBN-10: 1590597796) which I found helpful on a lot of these basic concepts. It was written for 6.06 and .20 but most of it is still relevant. The other thing that I found useful for determining if your tuner is working properly is tvtime. Just install it from the repos (sudo apt-get install tvtime) and run it. It's a very simple app that just allows you to watch tv, no pvr functions. If tvtime doesn't give you any video, your card is probably either not connected properly or is broken.
Well be careful saying that.  It supports analog cards without hardware encoders.  So if you have a PVR-XXX or any digital card, it won't work.

---

### Post by murchball on 2008-04-29
Thanks for the clarification, Superm1; I didn't realize that. I had hooked up a PCTV HD-5500 and was able to watch analog cable, so I figured it would work for any analog card. 

Sorry for the misinformation!

I believe I have used 
cat /dev/video0 > test.mpg
on a Hauppauge analog card to verify that it was working outside of Myth. The only problem with that is that it doesn't allow you to change channels.

---

### Post by gazer22 on 2008-04-29
> **murchball said:**
> I have used 
cat /dev/video0 > test.mpg
on a Hauppauge analog card to verify that it was working outside of Myth. The only problem with that is that it doesn't allow you to change channels.

Changing channels:
```
ivtv-tune -c9
```

It's part of the ivtv-utils package:

```
sudo apt-get install ivtv-utils
```

And, as murchball said, really helpful for debugging systems.

+1 on the Practical MythTV book.  My university library had a copy.  Worth every cent!  :)  Combined it with the mythbuntu manual (which is ever-evolving), and I was able to get a good grasp of what was going on.

---

### Post by Weidbrewer on 2008-05-12
Now, this might be too obvious, but I notice that it hasn't really been touched upon:  Before you set up your channels, how did you set up your card?

For example, although my PCHDTV 5500 is a digital card, I had it hooked up to analog cable (since I wasn't running through a cable box) like you are.  Therefor, I had to set it up as whichever was the default for analog.

Then, under channel set-up, I chose (I think, from memory) US-Cable from the drop down.  It was after I set these things that i was able to scan for channels.  Basically, it sounds to me like it's either A.) not seeing your card or B.) you have the wrong type of frequency specified.

(This tripped me up at first as well.)

---

