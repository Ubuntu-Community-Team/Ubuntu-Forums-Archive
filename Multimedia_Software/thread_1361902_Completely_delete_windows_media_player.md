---
title: "Completely delete windows media player"
date: 2009-12-22
forum: Multimedia Software
---

### Post by Nikoros on 2009-12-22
Hello,

I've really appreciated the help people have given me last time! I've got another question: lately I had tried to install windows media player 9, using Wine in Ubuntu. Well, it didn't work, so I have deleted it and thought: never mind...

But it didn't go away! Every time I try to open media files I get an errormessage like "File not found". I had to delete Wine completely and have reinstalled it... But it's still there! Every time I try to open a media file in Firefox or Opera it is opened with "a Wine application" (windows media player 9), which is long gone... How can I solve that? How can I make that "wine application" go away?

I really appreciate your help!

Kind regards,

Nikoros.

---

### Post by USB_NL on 2009-12-22
a quick sollution would be the 

MyPlayerConnectivity Add-on 

for Firefox

you can choose another player after installing

---

### Post by howefield on 2009-12-22
What's your preferred Multimedia application set to ?

System > Preferences > Preferred Applications 

And did you delete the wine folders in your /home directory as well as uninstalling wine.

Or try right clicking on a file that is giving you grief, and select Open with > Other application and make you choice. Does that work ?

---

### Post by Nikoros on 2009-12-22
Wauw, that were very quick replies! Thank you!

@USB_NL: I've tried that add-on. It now opens files directly, but I first used to get a choice: open instantly or download it. Some files (short sounds) I opened with VLC and big files (Jamendo-music) I downloaded to my harddrive. Now that possibility is gone :(.

@howefield: It's Rhythmbox. However, I only use it to listen music in my collection. I have also a download folder where I have all other sounds and music. I listen them using the VLC. I can do that in Nautilus with mp3 files. When I tried to play an avi file, it opened with media player. So I also set it to VLC and that worked. But do I have to do that to each particular media-filetype? Is there an option in VLC where I can set all mediafiles to be opened by VLC?

When I reinstalled Wine, I first removed it completely with synaptic and then deleted the ./wine folder and reinstalled it. But it seems like media player is still somewhere on my system and I really want to get rid of that 'Wine Application'. But... how?

Sorry for my bad English...

Kind regards,

Nikoros.

---

### Post by USB_NL on 2009-12-22
> **Nikoros said:**
> 
@USB_NL: I've tried that add-on. It now opens files directly, but I first used to get a choice: open instantly or download it.

You can make playlists with vlc to download it and watch your livestream at the same time.
just copy the mlr-streams save them as (dot)asf files and use that codec.

---

### Post by USB_NL on 2009-12-22
never heard of Jamendo

I do make music with PCsystems With ubuntu I can use Madtracker II thrue Wine to make music :P

---

### Post by HappyFeet on 2009-12-22
> **Nikoros said:**
> Is there an option in VLC where I can set all mediafiles to be opened by VLC?


Open your home folder and go to edit>preferences>media tab

---

### Post by Nikoros on 2009-12-24
> You can make playlists with vlc to download it and watch your livestream at the same time.
just copy the mlr-streams save them as (dot)asf files and use that codec. 

Thanks for the tip!

> never heard of Jamendo

That's a website where you can download a lot of free music!

> Open your home folder and go to edit>preferences>media tab

Thank you! That helped a lot!

Anyway, the problem is (nearly solved, or I can better say: it doesn't really bother me right now). Anyway, thank to you all, I don't have that problem any more in nautilus. The only thing is Firefox, but I've solved it somehow using this thread: [http://ubuntuforums.org/showthread.php?t=851300](http://ubuntuforums.org/showthread.php?t=851300) and especially this reply:

[ATTACH]141030[/ATTACH]

Then I could set the mime-types again and can now choose to use vlc-player to open all the media-files on the internet. That 'Wine Application' doesn't bother me anymore.

Thank you all for your great help!

---

