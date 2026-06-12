---
title: "How to make video out of Impress presentation?"
date: 2010-04-24
forum: Multimedia Software
---

### Post by azangru on 2010-04-24
Let's say you have a presentation made in OO.o Impress and you have an audio record of the speaker, and you want to combine these two together into a nice video consisting basically of the presentation slides and the speaker's voice - how would you do it?

Would you export the presentation to flash (.swf file), then import it in a video editor (if so. which one?)?

Or would you rather export slides to individual pictures and import them one by one to a video editor (again, which one?)?

Or would you do it differently? Perhaps you know of a handy howto? Could you please comment?

Thanks.

---

### Post by tom66 on 2010-04-25
You could try using a screen capture program such as gtk-recordMyDesktop, but for a long presentation you will have to wait a while, because it records exactly what is on the screen including all delays.

---

### Post by HermanAB on 2010-04-25
...or maybe use Istanbul.

---

### Post by P4man on 2010-04-25
gtk-recordmydesktop is a great app for this. Play the presentation while you record your audio and it will create a video from it on the fly.

I you want more control over timing and editing  and be able to to record audio parts easily, record the audio fragments for each slide using soundrecorder (or any other app), insert the sound files  in impress for each slide, and export the whole as flash video (never tried this though).

If you want to be able to speak over several slides and have full control, consider a videoeditor like pitivi to rearrange slides (exported to stills or movie clips from OO) and your sound clips.

---

### Post by azangru on 2010-04-25
> **P4man said:**
> If you want to be able to speak over several slides and have full control, consider a videoeditor like pitivi to rearrange slides (exported to stills or movie clips from OO) and your sound clips.

I actually have the talk recorded in an audio file already  :-) Just wanted to accompany it with the slides, and I thought a video editor would be a very convenient tool for this job. I didn't seriously consider a desktop recording program; perhaps I should. 

PiTiVi was the first video editor I tried, but I couldn't manipulate still images in it. I couldn't see where it placed the still images on the timeline and couldn't find an easy way to control the time for each still image to be shown. I then tried Cinelerra (which was complicated indeed) and Kdenlive, but thought that somebody over here must have already done this and could share their experience with me.

---

### Post by tuthmosis on 2010-07-04
I was also looking to do the axact same thing...

I was looking for an equivalent to Adobe Presenter.

I guess the best thing would have been to create an audio-less presentation in OO, export it to swf file then import that file as the visual source a video montage i would have edited using some Ubuntu app. (Adobe Premiere like)

Unfortunatly:
1) OpenOffice's developpement seams to have been dropped 7 years ago. Any animation or transition isn't exported to the swf file.
2) Pitivi doesn't import swf files and doesn't have transitions !
3) Kdenlive doesn't import swf files (But is 1000 times more promissing than pitivi !)

If anyone knows a good equivalent to Adobe Presenter but for the Linux OS... Please raise your hand !!!

---

### Post by tuthmosis on 2010-07-04
Thanks but this thread is about the need to create presentation that can be shared and viewed mainly online. (Or at least presentations to which audio could be added and synchronized.)

> **rabbitrun said:**
> If you download video from youtube and facebook, etc. try aneesoft video converter. 
It works good for me. I download video from different websites and aneesoft works very well. 
It converts video to WMV and AVI, and other formats. And it converts audio also to 
WMA, WAV, MP3, etc. There is an option I like, 'surf and catch video'. 
[http://www.*************/win-ipad-video-converter.html](http://www.*************/win-ipad-video-converter.html)

---

### Post by ron999 on 2010-07-04
@tuthmosis
That post you have quoted is just SPAM

---

### Post by tuthmosis on 2010-07-04
> **ron999 said:**
> @tuthmosis
That post you have quoted is just SPAM
That's what i thought !

---

### Post by ron999 on 2010-07-04
> **tuthmosis said:**
> That's what i thought !
So why did you quote it?

---

### Post by cghost on 2010-12-27
I'm in the exact same situation. Did anyone figure this out?

---

### Post by darkazurka on 2011-04-05
> **azangru said:**
> Let's say you have a presentation made in OO.o Impress and you have an audio record of the speaker, and you want to combine these two together into a nice video consisting basically of the presentation slides and the speaker's voice - how would you do it?

I'm afraid I have to press the "Print Screen" button to take screenshots of the images in the presentation. 2. Crop them with Shotwell (or GIMP) to only get the area I want 
3. Put the image in Pitivi and editing for how long(how many seconds) I want the image to show.
4. Manually add the audio I've recorded at certain intervals.

It means work anyway. No easy thing.

---

