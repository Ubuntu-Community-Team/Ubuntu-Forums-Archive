---
title: "Dark MPEGs - Weird Nvidia X Settings"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by galvheim on 2008-01-09
I have search and searched but are unable to find any answer on this issue.

I'm running Gutsy Gibbon with Compiz and Nvidia 8800 GTS.

Here's my problem:

My X Server XVideo Settings is set to:
Brightness = 0
Contrast = 4096 
In other words default settings.

BUT, everytime I load a .mpeg, .xvid, divx, or other file - either in a browser or from disk using Totem or VLC-player they will show up much darker than they should. In some cases it's so bad that it's not watchable. So what I have to do, is open the Nvidia-settings panel, and just by opening it it will suddenly show the video with normal light. It seems like when I close the configuration panel that it simply forgets my settings.

I have tried to load the settings using by loading the nvidia settings in sessions after startup. This worked fine for some other issues, but my problem with regards to dark video still persists. 

So how can I make sure that I save this settings? And how do I make Ubuntu not forget about these every time I play a video? 

I have tried to start the settings panel with this command:
$sudo nvidia-settings
By doing this I wanted to make sure that my settings had all permissions to be saved. Also saving to X Configuration Files have turned out unsucsessful. 

So here I am, asking for some good solutions to my problem. This has been very frustrating so far and I would love to see this get back to normal.

---

### Post by eye208 on 2008-01-09
> **galvheim said:**
> I have tried to load the settings using by loading the nvidia settings in sessions after startup. This worked fine for some other issues, but my problem with regards to dark video still persists.
Did you add "nvidia-settings -l" to your GNOME session startup programs?

---

### Post by galvheim on 2008-01-09
No, but I added this to my startup sessions:

   nvidia-settings --load-config-only

Shouldn't that do the trick? 
What seemss to be the problem is that ony the XVideo settings is off. When I close the settings and re-open again, then it's allways back to -96 giving me the darker. But this is only when I 'sudo' the settings-panel. When I open it normally from the drop-down-menu, it will suddenly load the settings and it says Brighness = 0. I also see this happening in the video playing at the same moment - how it changes from dark to bright...

---

### Post by galvheim on 2008-01-09
Even editing the file in my home directory named .nvidia-settings-rc , where I clearly find the line saying:

Ubuntu:0.0/XVideoTextureBrightness=-96

And set this value to zero and save it, will not help. As soon as I re-open a file it will automatically go straight back to: 'Ubuntu:0.0/XVideoTextureBrightness=-96' I must say that this is very strange.

Is it possible that my VLC-player is able to override and go into this file and set this value all by itself?

If thats the case, then I know what the problem is.

---

### Post by galvheim on 2008-01-09
Actually it did!!

I had my '.nvidia-settings-rc' open in Gedit while going through some settings in VLC, after saving these settings which had to do with brightness, Gedit suddenly told me that the file had been altered on my disk and asked if I wanted to re-load it. Suddenly the line 'Ubuntu:0.0/XVideoTextureBrightness' was back to zero!!!

:popcorn:

Very nice. My last option if it didn't work, would be to change the file and then just remove writable permissins for it. Thereby forcing it to my will.

Anyway, too bad I put all this in the forum, since it was solved so quickly. 
If it's possible to remove it, please do so...

Thanks anyway.

---

### Post by eye208 on 2008-01-09
I think you can also save the brightness/contrast/gamma settings in VLC. But the fact that VLC writes them to .nvidia-settings-rc is surprising indeed!

---

### Post by Garret88 on 2008-01-12
I have an nvidia 8800gts 640mb and also this problem but also if i open nvdia-settings the video is dark. Also editing the nvidia-settings-rc

Someone can explain how fix the problem?

---

### Post by galvheim on 2008-01-12
If you are running the Totem Media Player then go to (my player is in Norwegian so I can only guess what it would be in english):
Edit > Preferences > Screen

Then you will have a set of sliders controlling colorbalance. 
Set the brightness and contrast to the settings you like. Also the other sliders if its of any use for you. This will override the settings in for the .nvidia-settings-rc file and overwrite them. 

Tell me if this works for you. Sorry about the mistake above, since I was talking about VLC player and not Totem.

---

### Post by Garret88 on 2008-01-12
It works!! Thanks!!!

---

