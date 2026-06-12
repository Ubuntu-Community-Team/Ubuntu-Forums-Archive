---
title: "TIP: Putting the issue of ATI driver video tearing to rest...FINALLY!!!"
date: 2011-06-12
forum: Multimedia Software
---

### Post by framebuffer on 2011-06-12
For a long time, I have been having video and application tearing problems on ATI's proprietary drivers.

For me, its important to be able to watch HD videos on VLC, use Blender, Nuke and Houdini.

The problem with the open source driver was that it was not running Houdini at all, Blender was slow and the laptop was generating a lot of heat - somuchso that it blew my heatsync that I had to get replaced. But there was no video tearing.

The problem with the additional recommended driver by Ubuntu was that it was tearing videos and games. Plus, Houdini was not running.

I tried everything that I could Google but in vain. The problem was getting so annoying that I decided to switch to Mac OSX. I though I'd give it a last shot.

Trying to run Houdini forced me to upgrade from Catalyst 8.5 that ships with Ubuntu to 11.5. And who knew?

ATI has added a new "[Tear Free Desktop]("http://dolphinaura.com/home/9-linux/19-stepping-forward-atis-new-qtear-free-desktopq")" option in the Catalyst. Problem solved! :KS

Here's how to [Install]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20AMD/ATI%20Catalyst%2011.2%20For%20Ubuntu%2010.10%20Maverick") Catalyst 11.5

Imagine my happiness (after 4 years of using ubuntu) that I am now finally able to run everything the way I want!

Now, only if someone would simplify [dynamic graphic card switching]("https://help.ubuntu.com/community/HybridGraphics").

---

