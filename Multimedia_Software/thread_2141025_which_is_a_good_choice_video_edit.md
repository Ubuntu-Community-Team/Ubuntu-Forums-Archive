---
title: "which is a good choice video edit"
date: 2013-05-01
forum: Multimedia Software
---

### Post by mike acker on 2013-05-01
which is a good choice for a video edit

---

### Post by Stormlord on 2013-05-01
It depends on the level of professionalism you need.  Openshot is quite good if you require something not 100% professional.  Check it out.

---

### Post by Roasted on 2013-05-01
For basic videos, openshot.
For more advanced videos, kdenlive.

---

### Post by mike acker on 2013-05-01
thanks
i've tried OpenShot but it's not very intuitive....
i've installed the kdenlive i'll try that out
opefully i can collect clips of one sort or another, paste them into the stream and then export the stream in a format that...
-- if it's going to a windows user it may need to be .avi rather than .mp4

i need a compact format though, not .mov

---

### Post by LuridCinema on 2013-05-02
Lightworks just dropped for Linux. Industrial strength and has been used to edit many feature movies if you are willing to learn it..highly recommended. With video editing / production, it does not matter what the output is so much from the editor. You can use ffmpeg or Handbrake to transcode to get whatever format you need

---

### Post by mike acker on 2013-05-02
> **LuridCinema said:**
> Lightworks just dropped for Linux. Industrial strength and has been used to edit many feature movies if you are willing to learn it..highly recommended. With video editing / production, it does not matter what the output is so much from the editor. You can use ffmpeg or Handbrake to transcode to get whatever format you need

thanks

what i'm mainly interested in is sharing video -- either .mov from a camera or -- mp4 from our Kazam screen caster . some folks would probably use YouTube but I prefer not to do that .  The Ubuntu1 share area will do just fine .

so i'm interested in a compact format,-- that,-- generally other systems can read.   the one that makes the most sense is webm

i think people should be able to read it with a browser but i've not had much luck .   right now i'm suggesting windows users install VLC
i tried VLC on my Win7 box and it seems to be much better that the other "standard" software, -- VLC just plays the media you tell it to,-- nothing more, -- and it seems to play just about anything .

i'm working with OpenShot right now, trying to experiment with various forms.

it seems that if I keep the demo window on my system a little bit undersized, and then using Kazam -- select just the window i'm doing the demo in -- and then reformat the result as 1920x1080p using OpenShot -- I get a pretty decent presentation on the receiving system -- using VLC .

i wish Kazam had an audio VU indication though,-- it's easy to set the audio input option wrong and end up with no audio ,--

---

### Post by LuridCinema on 2013-05-02
I'll second Openshot or Kdenlive for more basic stuff. Plenty of howto videos on YouTube.

Problem is that video editing and sharing is complicated. We like simple especially if we are not wanting to do high end stuff. The fact remains that cameras give us one format, editors sometimes like another, and then YouTube likes another. I have been using Cinelerra for years. Im able to edit the native format from my video cams, but I have to compress using ffmpeg to get it optimized for YouTube. I just installed Lightworks and I am in the process of learning that. I will prolly stick w/ Cinelerra for a while till I get the hang of Lightworks. might take a few weeks.

Good Luck.









.

---

### Post by mike acker on 2013-05-04
> **LuridCinema said:**
> I'll second Openshot or Kdenlive for more basic stuff. Plenty of howto videos on YouTube.

Problem is that video editing and sharing is complicated. We like simple especially if we are not wanting to do high end stuff. The fact remains that cameras give us one format, editors sometimes like another, and then YouTube likes another. I have been using Cinelerra for years. Im able to edit the native format from my video cams, but I have to compress using ffmpeg to get it optimized for YouTube. I just installed Lightworks and I am in the process of learning that. I will prolly stick w/ Cinelerra for a while till I get the hang of Lightworks. might take a few weeks.

Good Luck.


thanks

I'm going to experiment more with the webm format

if i understand things properly webm is the format to be used with html5
i ran a test just now and found that my Firefox v.20 can play the .webm data i've created
so now i need to test to see if any of the IE browsers can do it .    Chrome also works on Linux.
I couldn't find any program on Win7 that could play the file ( except VLC -- which I had installed but which most users don't have ) .

i suspect there a problem between msft and linux versions of .webm data
as i'm fiond of noting: computers have no trouble talking to each other
the problem is : people don't talk to each other and are fond of distorting each other's messages .

See also: [http://www.any-video-converter.com/webm-to-windows-movie-maker.php](http://www.any-video-converter.com/webm-to-windows-movie-maker.php)    ( yuck )

---

### Post by The Spectre on 2013-05-04
> **mike acker said:**
> which is a good choice for a video edit

Here is another Simple Video Editor for you to check out...
[http://www.pitivi.org/](http://www.pitivi.org/)

---

### Post by mike acker on 2013-05-04
> **The Spectre said:**
> Here is another Simple Video Editor for you to check out...
[http://www.pitivi.org/](http://www.pitivi.org/)

yes!! thanks!!   I tried that one
I'm going to stick with OpenShot for the moment because as noted: i need to find a format that works well for sending to windows users. OpenShot allows me to select from quite an assortment of container options for the video codec and the audio codec  as well as video format .
 
i think an .avi container with h.264 encoding might be the best choice

one thing is getting the transfer to work at all; the next problem is in getting it to work well enough as to be useful

in my screencast (Kazam) I select an area smaller than the total screen,  by just rezizing my browser (or other presentation) and then mapping Kazam over that area

now the selected area should play back as shown on the destination system 

so we select a 1920x1080p format for the container . i finally did get this to work using an mpeg container but the windows media player made a mess of the job having a bad case of the jitters .  ( VLC played it perfect ) .

it seems clear to me we are into another format war here. (whoever can make their format the winner gets to sue everyone else for patent infringement. go goons. ) the stakes are enormous as it now appears internet video and voip are going to wipe out cable tv.

---

### Post by houseisland on 2013-05-04
Thanks.  

Now I do not have to start a thread asking the same questions.

:)

---

### Post by jpaulb on 2013-05-04
> **LuridCinema said:**
> Lightworks just dropped for Linux. Industrial strength and has been used to edit many feature movies if you are willing to learn it..highly recommended. With video editing / production, it does not matter what the output is so much from the editor. You can use ffmpeg or Handbrake to transcode to get whatever format you need

I have been playing with it for a couple of days. So far I prefer it anything else I have tried including "Final Cut" on the Mac and  Adobe on Windows.:D

---

### Post by cibalo on 2013-05-08
Hello,

> **mike acker said:**
> a good choice for a video edit

avidemux + k3b

---

### Post by sdowney717 on 2013-05-08
kdenlive was the only one that did what i wished.
I tried many of them and most were primitive or crashed.

---

### Post by Rob Sayer on 2013-08-10
> **mike acker said:**
> ... i think an .avi container with h.264 encoding might be the best choice....

*Bad* idea.  That container doesn't support all h.264 features.  Sorry, but seeing an avi file with h.264 video within is a sign the encoder didn't know what he/she was doing ....

---

