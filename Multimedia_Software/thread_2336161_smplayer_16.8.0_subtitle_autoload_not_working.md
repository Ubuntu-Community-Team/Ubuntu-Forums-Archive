---
title: "smplayer 16.8.0 subtitle autoload not working"
date: 2016-09-05
forum: Multimedia Software
---

### Post by michaelbr on 2016-09-05
Hi:
I'm using Smplayer 16.8.0 with Ubuntu 16.04, in Smplayer I've configured to autoload subtitles with the same name as the movie, but whenever I load a media file (mp4, mkv, etc.) with subtitles, the media file started with no subtitle, I have to add it manually. Is this still a bug or I'm missing something here?

---

### Post by SeijiSensei on 2016-09-05
Most Matroska (.mkv) files have the subtitles embedded within the container along with the video and audio.  Usually you don't need to do anything other than open the file in SMPlayer. Same is true for .mp4 files with embedded subtitles.  In Options > Preferences > General > Preferred Audio and Subtitles I have "jp|jpn" in the Audio box and nothing in the Subtitles box.  I also have the audio and subtitle tracks set to 1.  When I open an anime .mkv file, it usually plays the Japanese audio and shows the English subtitles.  Sometimes I have to select the subtitle track manually from the drop-down box at the top of the SMPlayer screen.

Is that what you mean by "autoloading," or are you talking about loading separate subtitle files in a format like .srt or .ass?

I'm using 16.1.0 from Doug McMahon's [PPA for Trusty]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media"), but I don't recall this behavior changing over the years that I have used SMPlayer.

---

### Post by michaelbr on 2016-09-06
> **SeijiSensei said:**
> Most Matroska (.mkv) files have the subtitles embedded within the container along with the video and audio.  Usually you don't need to do anything other than open the file in SMPlayer. Same is true for .mp4 files with embedded subtitles.  In Options > Preferences > General > Preferred Audio and Subtitles I have "jp|jpn" in the Audio box and nothing in the Subtitles box.  I also have the audio and subtitle tracks set to 1.  When I open an anime .mkv file, it usually plays the Japanese audio and shows the English subtitles.  Sometimes I have to select the subtitle track manually from the drop-down box at the top of the SMPlayer screen.

Is that what you mean by "autoloading," or are you talking about loading separate subtitle files in a format like .srt or .ass?

I'm using 16.1.0 from Doug McMahon's [PPA for Trusty]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media"), but I don't recall this behavior changing over the years that I have used SMPlayer.

Thanks SeijiSensei for your reply, sorry for the misunderstanding, what I meant is loading an external subtitle file, such as .srt or .ass, I'm not using Ubuntu at this moment, I think in Preference > Subtitle > there's an option called Autoload subtitle, under it there's a drop down list, with 2 options, The same name as the movie and the other is First available subtitle (sorry, I can't recall exactly the wordings), and I chose the same name as the movie (my subtitle and movie has the same name), but whenever I'm clicking a movie, it came up showing subtitle NONE, so it seems to me that the configuration in Preference is not working, even when there's an embeded subtitle, when I click subtitles (the right most option in the menu), it showed the embeded one, and my external, but none of them are chosen.

---

### Post by SeijiSensei on 2016-09-06
I only have one video with a separate subtitle file (in .srt), and SMPlayer launches both the video and subtitle files simultaneously.  I'd check the file names to make sure they are identical.  Or try renaming both the video and subtitle file to something simple like myvideo.mp4 and myvideo.srt and try that.

What player are you using for the engine?  I use mpv nowadays, but when I used mplayer I didn't have a problem then either.

In Options > Preferences > Subtitles I have "All subs containing movie name" in the drop-down box and "Select first available subtitle" checked.

---

### Post by michaelbr on 2016-09-07
Thanks for your reply, I'm using mplayer as engine, and I always make the names identical, I've been using smplayer for some time, and it never loaded subtitles automatically. Maybe I'll try your PPA.

---

### Post by SeijiSensei on 2016-09-07
> **michaelbr said:**
> Thanks for your reply, I'm using mplayer as engine, and I always make the names identical, I've been using smplayer for some time, and it never loaded subtitles automatically. Maybe I'll try your PPA.

That's only for Trusty (14.04).  For 16.04, use this for mpv: [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

You can also use rvm's own PPA for smplayer: [https://launchpad.net/~rvm/+archive/ubuntu/smplayer](https://launchpad.net/~rvm/+archive/ubuntu/smplayer)

---

### Post by michaelbr on 2016-09-08
> **SeijiSensei said:**
> That's only for Trusty (14.04).  For 16.04, use this for mpv: [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

You can also use rvm's own PPA for smplayer: [https://launchpad.net/~rvm/+archive/ubuntu/smplayer](https://launchpad.net/~rvm/+archive/ubuntu/smplayer)

Thanks so much for your reply, it's working now, I have no idea why, did not replace the apps, but tried several different configurations and now it's working. Thanks so much for you tips and help.

---

