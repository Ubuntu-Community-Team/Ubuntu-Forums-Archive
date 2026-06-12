---
title: "Good sound editor for videos"
date: 2012-11-22
forum: Multimedia Software
---

### Post by unknown user on 2012-11-22
I have a number of videos that I have added intros to. These intros last for a few seconds and have sound on them. I do not want the sound though, just a video, no sound. 

I have used PiTiVi Video Editor and was able to highlight the section and then move the sound bar down so it was like there was no sound. However, there must be a better way and it then jumps to a high volume after intro is over. 

Is there a way to remove sections of sound and then to have the sound fade in after the section of removed sound? I have just read about cinelerra, has anyone done this with it?

---

### Post by unknown user on 2012-11-25
2 Days, 104 viewers and not one person can offer anything??

---

### Post by vanadium on 2012-11-25
In the most simple of editors, e.g. openshot, one can fade in/out sound for clips. However, I may not have understood your particular issue well.

---

### Post by Unterseeboot_234 on 2012-11-25
Cinelera is my goto video editor. I run Ubuntu AMD64 and that, I think, keeps the crashes away which seems to be the major complaint from some folks. I do all my editing using dvRAW codec and save as dvRAW which creates massive storage issues.

You have to learn how to use Cinelera. The tutorials available are too technical. Basically, you import your footage as "assets". Select an asset, drag the icon and trim in the left-hand editor window. Once those trim points have been determined, then you add to the timeline. The trims and add-to-timeline are buttons in the editor window.

Different codecs require sound to export. Other codecs you do as two passes and therefor you wouldn't do the audio step. I have exported dvRAW, then reclaim as a footage back into the assets. I deleted the audio with a select and delete upon the audio track in the timeline.

The timeline is very interactive. You see the audio as a spectrum on its own track. You can add sound and/or video channel tracks. You can add keyframe points to a volume line that rides at the top of the audio channel and then drag the point vertically to adjust volume. The hard part is you must activate and de-activate all the timeline tracks whether they are live and editable, e.g. you have to remember to turn off video track 1 to make local changes on audio2 and audio3.

But, in short, you get linear visual manipulation of audio. Viewers of my work remark how good the sound is and that's because Cinelera is processing 64-bit information -- the only audio engine I'm aware of doing that.

Finally, there are plug-ins for some special-effect audio. I've never tried them.

---

### Post by unknown user on 2012-11-26
Hi guys, thanks for your reply, it is a great help. I have Cinelera , but I think it is going to take me a bit of time to get used to it. I will have to give that a try over the next coming weeks to get my head around it. 

Thanks again for the advice and replying to this thread.

---

### Post by azmyth on 2012-11-26
You can do it with Lives video editing software as they have fade in and out.

[http://lives.sourceforge.net/](http://lives.sourceforge.net/)

You could even export the audio and edit it with something like Audacity and the import back in.

You could also do it with Cinderella as well.

---

### Post by AstroLlama on 2012-11-27
you could use ffmpeg to reencode the video without sound. this would strip the sound permanantly off the clips. transmageddon GUI application can also transcode the video and ignore sound. give it a go!

---

### Post by sudodus on 2012-11-27
> **vanadium said:**
> In the most simple of editors, e.g. openshot, one can fade in/out sound for clips. However, I may not have understood your particular issue well.

I use OpenShot to edit the videos from my camera.

It is rather easy to do mute the clip in OpenShot, and it is also easy to cut a clip into pieces, where you can mute the intro piece and use the audio track of the other piece(s).

---

### Post by unknown user on 2012-12-05
Thanks for that guys, it is a great help. I will be looking more into this over the Christmas break, so I may have to follow up with a few :)
Thanks again

---

### Post by SeijiSensei on 2012-12-05
What container are the videos in?  If you're using the Matroska container, you can just pull apart the streams with mkvtoolnix then reassemble the video without the audio track.

Mencoder will let you convert a video without the audio as well.  

Both mkvtoolnix and mencoder are in the repositories.

---

### Post by markosjal on 2012-12-05
SInce you are asking about a sound editor and not a video editor I recommend the almighty Audacity . I have demuxed audio from edited video changed levels and cleaned up noises then laid it back to the video by remuxing Generally I found I came up one frame or less short on the audio when it was laid back for some reason but it works and is the best way to edit audio for the video as long as you can premix the basic mixing you need and you can always layback more tracks in audacity or video editor. 

If you are careful to not resaple in audacity you can ping pong it back and forth many times with no loss.

ANyone seriously editing should use audacity.

---

