---
title: "Convert mkv files to differnt resolution to play in a TV"
date: 2012-04-01
forum: Multimedia Software
---

### Post by arysar on 2012-04-01
I have some mkv files encoded with h264, 960x720 that can't be played on my LG TV, I want to convert to 720x480 or 1280x692 because I know that these resolutions work well. I've try with 

[http://ubuntuforums.org/showthread.php?t=1566035 ]("http://ubuntuforums.org/showthread.php?t=1566035")

but get some errors like "error, non monotone timestamps 192 >= 192 av_interleaved_write_frame()" and I have no luck with avidemux either. ¿there is some other way to change the resolution?

Thanks!

---

### Post by Claus7 on 2012-04-01
Hello,

are you sure that the problem is the resolution? How did you decide that this is the reason your files are not played from your tv? Have you tried to use a file that you indeed are able to play with your tv and simultaneously you can find information from an ubuntu box?

I mean: check a file that you can play on your television, transfer it to ubuntu and check out preferences.
Then compare these ones with the files that are reluctant to play on your telly. With this procedure you will be able to say which is the real reason that your television cannot play some of the files you mention.

Why did you fail with avidemux? Have you checked the properties of the converted file? Are you sure that your conversion has those codecs that your telly supports?

Some ideas here,
Regards!

---

### Post by lovinglinux on 2012-04-01
I would try [Handbrake]("http://handbrake.fr/downloads.php"). This is the best video conversion and ripping tool I have used with Ubuntu.

After loading the video, click the "Picture Settings" button. In the Storage options select "Custom" and untick "optimal for source". In the Display options untick "Keep Aspect". Change the resolution in the Storage options.

---

### Post by papibe on 2012-04-01
> **lovinglinux said:**
> I would try Handbrake.
+1

I would suggest install it following these steps (from a ppa).
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk
```
Hope it helps.
Regards.

BTW, I don't understand the reason why you need the conversion. Are you going to playing on of those set-top media players that only play a limited formats?

---

### Post by arysar on 2012-04-02
> **Claus7 said:**
> Hello,

are you sure that the problem is the resolution? How did you decide that this is the reason your files are not played from your tv? Have you tried to use a file that you indeed are able to play with your tv and simultaneously you can find information from an ubuntu box?

I mean: check a file that you can play on your television, transfer it to ubuntu and check out preferences.
Then compare these ones with the files that are reluctant to play on your telly. With this procedure you will be able to say which is the real reason that your television cannot play some of the files you mention.

Why did you fail with avidemux? Have you checked the properties of the converted file? Are you sure that your conversion has those codecs that your telly supports?

Some ideas here,
Regards!


Well that is what I did, I have several mkv files encoded with h264 with resolutions of 720x480 or 1280x692 1280x720 and they all play well in the TV, the only that do not play are those with 960x720 so I think that the problem is resolution.

Anyway I finallly figure out how to doit with avidemux, I'm sorry it was a silly thing. The problem was that I changed the resolution manually and when click apply the numbers change to the original value, I have to chagne the aspect-ratio and it worked.

Thanks

---

