---
title: "Video quality integrated vs. separte video card??"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by tegwilym on 2008-01-14
Got a question about video if anyone has some ideas. 

I'm running a MythTV setup and got it all working pretty good. I built a dedicated machine as a media computer.  I forget the exact model, number, but I'm running an Asus motherboard that has a built-in video card that has component, S-video, composite, vga...etc outputs.  I have my TV connected to the component side since I want the best picture I can get.  

The image is slightly blurrier using the computer than it is without the computer.  I hook it up like this, so I shouldn't have any signal loss -

Directv box --Svideo-->input on capture card-> Component video-->TV

If I bypass the computer and do it the 'old way' I'm doing this:
Directv--S-video-->Receiver for switching-->S-video-->TV

the only thing I'm doing different is that I'm using component out rather than S-video.  

Same thing when using the DVD player. which I would use component video dircectly to the TV.
If I play a movie on the X-box 360 and compare it with the MythTV box, the X-box totally kicks the Myth's image in quality. 

Could I have better results if I used a separate card rather than the integrated video?  Haven't tried yet, but just wondering if anyone knew.  I only use Nvidia chipset for video since it just works for everything in Linux.  

Tom

---

### Post by ijason on 2008-01-14
hmm. i'm not entirely certain, but i believe your problem may be the video cables. the Svideo cables are more limited in their frequency response, so you'll generally get a clearly picture quality through component video. 

it also may be that the component output on your computer isn't pushing the same resolution that your xbox is, i'm not entirely sure how to check that. 

if your xbox and cable-box are pushing 1280 lines of resolution, but your computer is only able to output 740, you'll be able to see the difference if you have an HD tv.

does your mythbox have a component input?

---

### Post by tegwilym on 2008-01-14
> **ijason said:**
> hmm. i'm not entirely certain, but i believe your problem may be the video cables. the Svideo cables are more limited in their frequency response, so you'll generally get a clearly picture quality through component video. 

it also may be that the component output on your computer isn't pushing the same resolution that your xbox is, i'm not entirely sure how to check that. 

if your xbox and cable-box are pushing 1280 lines of resolution, but your computer is only able to output 740, you'll be able to see the difference if you have an HD tv.

does your mythbox have a component input?

I have my xorg.conf set to 1080i for the tv. I'll have to check the resolution settings again and see what I have there.  I'm using the Nvidia 9755 driver,  had trouble trying to upgrade to the newer one, but will have to try that again.  Maybe if I'm going in on S-video and out on component, I could be losing something in between.   But the quality looks great on the tv when I just go direct with S-video.
I do have good quality cables too.  Not the super spendy Monster cables, but better than the lousy stuff that comes with a video card. 
don't have component in on the card, so that's not an option.

---

### Post by ijason on 2008-01-14
hmm. firstly, YES... the super spendy monster cables are a total sham, anything above the absolute cheap OEM cables should be fine. it's all a copper wire carrying a signal, there's no need to pay through the nose. 

clearly, if the picture quality degrades when the computer is in the mix, you've found the culprit. it could be that the component-output from your computer isn't quite up to par of your xbox... which, doesn't sound that un-reasonable. however, if you're satisfied with the clarity of running direct Svideo between the cable box and the tv, maybe you should use the s-video output from your computer as well.

it might be something going weird when the video card outputs to the component, it may be pushing signal out the svideo port without the same problem :)

---

### Post by tegwilym on 2008-01-14
I was kind of also wondering if I had some signal loss between the motherboard and the video output riser card. There is a little ribbon cable between the two, but if it's a digital signal from the board to the riser, that shouldn't make a difference.  But if it was analog, there could be some loss there.   That's why I was thinking of trying my separate card to bypass that little bit maybe.

I'll have some more messing around to do with this thing though.  I've been happy with it so far, and even more pleased that I got it ALL working!  The serial to IR emitter for the DirecTV was a pain, but I  have a good idea how that works now. 

I should mention that I'm running this on MythDora rather than Mythbuntu <ducks>
But I want to go back and try the Mythbuntu again now that I figured out some of the problems.  the 'buntu version just boots up much faster!

...and hey, it doesn't have the Microsoft logo when I boot up - even BETTER!   :)

Tom

---

### Post by tegwilym on 2008-01-24
I just bought an ASUS 7200 PCI-e with the Nvidia chipset last night.  Turned off the on-board video and gave it a try.  All works, but picture quality still a little blurry looking, and the dvd playback still stutters a little.  Not fixed yet. 

Thinking maybe my dvd player was just a bit too cheap maybe and I got what I paid for?  This is the drive I got - [http://tinyurl.com/33ewuy](http://tinyurl.com/33ewuy)
OEM thing with no frills.

Tom

---

