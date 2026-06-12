---
title: "SMplayer options not being retained"
date: 2011-12-22
forum: Multimedia Software
---

### Post by Robbyx on 2011-12-22
Smplayer---Preferences---Advanced---options for Mplayer---video filters, is where I have put the following filter commands:

deblock,denoise_normal,deinterlace_lb

When I exit and go back into smplayer the settings have not been retained. How do I make the changes permanent?

---

### Post by SteveDee on 2011-12-23
> **Robbyx said:**
> ...When I exit and go back into smplayer the settings have not been retained...

Not sure why this is not working for you.

There should be a config file in your home directory, something like: /home/robbyx/.config/smplayer/smplayer.ini
(you need to show hidden files in your file manager to see this).

Try entering your settings in smplayer then open the smplayer.ini file. In the advanced section you should see your settings, example:-
[code]

freetype_support=true

[advanced]
color_key=20202
use_mplayer_window=false
monitor_aspect=
use_idx=false
mplayer_additional_options=
mplayer_additional_video_filters=deblock
mplayer_additional_audio_filters=
log_mplayer=true
log_smplayer=true

[\code]

If smpayer.ini does not exist, you could try un-installing smplayer then re-installing.

If smplayer.ini does exist, but your changes are not being saved, there may be a Permissions issue with this file.

---

### Post by Robbyx on 2011-12-25
I edited smplayer.ini in .config/smplayer and added the following adjustment:

mplayer_additional_video_filters=deblock,postprocessing,upscalling,denoise_normal,deinterlace_lb

I reloaded the ini file to check that it was still there after I had closed it. It was there.

The additional options are not appearing in the advanced options for smplayer! Can you suggest why?

---

### Post by SteveDee on 2011-12-27
> **Robbyx said:**
> ...The additional options are not appearing in the advanced options for smplayer! Can you suggest why?

From your other post([http://ubuntuforums.org/showthread.php?t=1898973](http://ubuntuforums.org/showthread.php?t=1898973)) it looks like it could be installation related. But to diag your smplayer problem I'd start by checking whether smplayer is actually using your Home smplayer.ini file. So make some simple config changes and see if any of them are stored in this ini file (i.e. not just the complicated filters config you mention).

If no smplayer changes are saved, try un-installing/re-installing smplayer.

If some changes are being saved (but not to your smplayer.ini) then look for another copy of smplayer.ini on your system and test that.

If some changes are being saved to your home system.ini file but not others, you probably need to check you have the right version for your release....and you probably need to post more details of your ?buntu type & version, and the smplayer version you are running.

---

