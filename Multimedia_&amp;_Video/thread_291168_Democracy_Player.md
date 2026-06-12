---
title: "Democracy Player"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by englishmen on 2006-11-02
Hi all, i was hoping to use Democracy Player for audio and video rss feeds as i did in Xp. I'm having a few problems and all tho ive asked on the Democracy Player forums most users over there seem to be windows users and cant really help, i hope some of you can.

None of the videos/audio i download with democracy player are playable, i click play and the progress bar says say 5 minutes and just zips along in seconds and there is not even a glimpse of a video/audio.

Also anyone know why after i installed democracy player do i all of  a sudden have "Mozilla web browser" and "Mozilla composer" listed under "internet" in my menu? Im new to ubuntu/linux in but i sort of get that's apps have dependencies, but its new to me that they require the complete gui of other apps :-k .

---

### Post by Archmage on 2006-11-02
To answer your second part:
Democracy use the Mozilla-Browser for displaying the webpages within the player. (E.g. the webpage with all the channels that you can subscribe.)

---

### Post by englishmen on 2006-11-02
I thought as much but do i really need the complete gui as well?

---

### Post by engla on 2006-11-04
That's either a packaging, programming or otherwise problem. Democracy player should work with either firefox, xulrunner or mozilla-browser and not need any specific of those. It could be as simple as that the packager didn't set up that as an "alternatives dependency"

---

### Post by englishmen on 2006-11-04
Thanks, would you or anyone else know how i can set it up correctly i.e. without Mozilla browser & composer and with video/audio playback actually working?

Thanks

---

### Post by engla on 2006-11-06
Hey I don't know much about the sound issues at all, but you can always try a later version. Ubuntu edgy has 0.8.x (something on 0.8) from the repositories, but the people at getdemocracy.com actually have a later version (0.9.1) packaged for ubuntu. You should be able to uninstall mozilla and democracy in ubuntu, and then install the package downloaded from their website.

That should fix the mozilla issue, but it's only chancing about the sound of course -- I haven't tried 0.9.1 myself since they don't provide a ppc version (and I didn't succeed in compiling my own)

---

### Post by englishmen on 2006-11-06
Thanks for the suggestion, i just download the latest version from the official  site and still Mozilla composer and web browser are being installed and still no playback of video or audio is working.

Is anyone using 0.9.1 successfully?

---

### Post by abbot on 2006-11-07
i've never got democracy player to work under ubuntu.  it always crashes as soon as it opens, both in dapper & now in edgy.

plus when you try to install 0.9.1 it conflicts with j2re and wants to uninstall it!  i'd rather keep my java thanks.  plus there are h.264 playback issues. I'll just use other programs to download & watch my videocasts as democracy is clearly underdeveloped for ubuntu.

---

### Post by Archmage on 2006-11-08
I did manage to make the default democracy player in Edgy work. You just need to install all the codecs. I forget this step, because I used Mplayer only for playing and therefore don't need any codecs.

Here is the link to install all the necessary codecs:

[Ubuntu_Edgy#How_to_install_Multimedia_Codecs]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs")

---

### Post by englishmen on 2006-11-09
I just got the codecs required via easyubuntu and now audio/video playback works. Why on earth democracy player doesn't come with the required codecs i don't know.

I get that democracy player needs components from mozilla to render the channel guide etc, but as ubuntu comes with firefox does it not contain the required components?

Thanks

---

### Post by Sir Frederic on 2006-12-10
> **englishmen said:**
> I just got the codecs required via easyubuntu and now audio/video playback works. Why on earth democracy player doesn't come with the required codecs i don't know.
Thanks

Unfortunately the codecs you need _are *not*_ open source. Both Ubuntu and Democracy player _*are*_ open source; this means that neither will install non-open source codecs on your computer. e.g. in windows and mac democracy does not install the required codecs, it simply uses those already enabled on the system.

It is a bit of a pain I know, but the codecs are easily installable. ( [http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs) ).

Cheers and good luck!

---

