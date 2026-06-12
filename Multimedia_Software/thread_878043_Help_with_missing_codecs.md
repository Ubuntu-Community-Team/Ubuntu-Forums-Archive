---
title: "Help with missing codecs"
date: 2008-08-02
forum: Multimedia Software
---

### Post by shufflemoomin on 2008-08-02
I am trying to get a video file to play which is of .mov filetype and uses the WMV3 and WMA2 codecs. When I try to open the file in Movie Player it tells me that I don't have any of these codecs installed. I've installed every codec I can find. When I run it with Mplayer from the terminal, it tells me it can't find wmvdmod.dll or wmv9dmod.dll. These files are in usr/lib/codecs, usr/local/lib/codecs and usr/lib/win32 but nothing will find them. Do I have to put these files elsewhere or install something that I'm missing?

Any help will be greatly appreciated, I've been trying to open this file for days.

---

### Post by jualin on 2008-08-02
[Check this website]("https://help.ubuntu.com/community/RestrictedFormats#Video"), it contains most codecs that you might need in Ubuntu.

---

### Post by shufflemoomin on 2008-08-02
I've added the restricted packages and the W32 codecs. I can't find anything to install that I haven't done already. It seems the files I need are there, it's just nothing is finding them.

---

### Post by jualin on 2008-08-02
Are you using Totem (Gnome default player) or MPlayer (KDE)?

---

### Post by shufflemoomin on 2008-08-02
Thanks for the reply:

I am on gnome and using totem. I was using the gstreamer backend which told me I was missing codecs and would do nothing. I read one of you other posts where you helped someone move to the xine backend. I tried that. I don't get a message about missing codecs with the xine engine, but nothing is displayed and the seek bar runs at high speed and nothing else happens. On the properties side panel, both Audio and Video codecs are listed as N/A.

Running the video from the terminal with MPlayer still shows that I'm missing codecs, even though I know the files are there.
Is there anything I might be missing somewhere?

---

### Post by jualin on 2008-08-02
Did you remove the "totem-gstreamer" package?

---

### Post by jualin on 2008-08-02
And also, remember that you need to restart Firefox every time you make a plugin change like changing from xine to gstreamer. The other person that I was helping solved his problem by restarting his Firefox.

---

### Post by shufflemoomin on 2008-08-02
> **jualin said:**
> Did you remove the "totem-gstreamer" package? I did. I've been using firefox on and off so I've restarted loads. Not sure how that would help. It's not a network video I'm trying to watch, it's a local file. Any other ideas on how I might get this working or anyone know why mplayer thinks codec files are missing when I know they're there?

---

### Post by jualin on 2008-08-02
> **shufflemoomin said:**
> I did. I've been using firefox on and off so I've restarted loads. Not sure how that would help. It's not a network video I'm trying to watch, it's a local file. Any other ideas on how I might get this working or anyone know why mplayer thinks codec files are missing when I know they're there?

Sorry I thought it was an internet video. If the video is in your computer you can try using VLC Player. With VLC you don't have the codec problems since you can play most files with it. Install it via terminal > sudo apt-get install vlc or via Synaptic Package Manager searching for the "vlc" package.

---

### Post by shufflemoomin on 2008-08-02
THanks again for the reply. I should have mentioned that I'd tried VLC. It's my player of choice on all other platforms I use. VLC acts like it's playing the video, the seek bar show the correct length and moves along, but doesn't display and video or audio. The stream info shows all the correct information, but it just doesn't play.

Is there anything else you think I could maybe try?

---

### Post by jualin on 2008-08-02
My last resource would be using Mplayer instead as your media player. You should be able to find the package on Synaptic

---

