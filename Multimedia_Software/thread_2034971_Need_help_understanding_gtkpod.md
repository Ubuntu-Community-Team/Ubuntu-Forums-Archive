---
title: "Need help understanding gtkpod"
date: 2012-07-29
forum: Multimedia Software
---

### Post by ratcheer on 2012-07-29
I see a lot of threads about iPods and iPhones, etc, but I haven't yet seen one that addresses the kind of questions I have.

I have installed and configured gtkpod. I have successfully mounted my iPod. I have followed the gtkpod documentation to import the music from the iPod to a local directory. But, the import is only partial in at least two ways:

1) My iPod (an iPod Video, 30GB) has 1088 songs on it. After running the import, my directory on my hard disk has only 992 files. Why aren't all of the songs imported?

2) Then, I click on the "Music Library" and there is nothing in it. That seems pretty stupid. So, I hunt around and find that I can add the directory to the Music library. I do so, and the Music Library gets only 179 songs. What on earth is going on?

In summary, gtkpod does not seem to do a very good job of what it is supposed to do (managing the iPod's music library). It doesn't import but a little over half of the music on my iPod, and of what it did import, it only puts about 20% into its local Music Library repository.

What am I missing? What good is gtkpod if I cannot manage all the songs?

Tim

PS - Here is an old thread that hints at a similar problem, but I'm not sure it was exactly the same. The thread died with no solution.

[http://ubuntuforums.org/showthread.php?t=1910343](http://ubuntuforums.org/showthread.php?t=1910343)

---

### Post by ratcheer on 2012-07-29
Sorry, I must have had a brain fart. 992 out of 1088 songs is a lot more than half. But still, it didn't import all of them.

Tim

---

### Post by ratcheer on 2012-07-29
Here is what is happening with it only bringing 179 of 992 songs into the Music Library. The 179 are all mp3 files, while the other 813 are m4a's.

So, gtkpod does not handle m4a's, Apples iTunes native filetype. That makes gtkpod totally useless. I guess I will have to uninstall it and look for another solution. :o

Tim

---

### Post by gordintoronto on 2012-07-29
Did you install an m4a codec? It might be included in the Ubuntu Restricted Extras.

I'm currently playing an m4a in Movie Player, using Linux Mint 13 with Cinnamon. I couldn't find a free one to download, so I used Sound Converter to create one.

---

### Post by ron999 on 2012-07-29
> **ratcheer said:**
> ... So, gtkpod does not handle m4a's, Apples iTunes native filetype...


Hi
With gtkpod, use
**Edit** > **Preferences** > **Installed Plugins**
Make sure that "**M4A File Type Plugin**" is ticked.

I can add alac m4a files into the Music Library and play them with the built-in player.:D
I can add them to my iPod, but it won't play them because it's only a Shuffle.:P

Using gtkpod-2.1.3~967887e compiled from git.
And Precise Pangolin-12.04

---

### Post by ratcheer on 2012-07-30
> **ron999 said:**
> 
With gtkpod, use
**Edit** > **Preferences** > **Installed Plugins**
Make sure that "**M4A File Type Plugin**" is ticked.



Thanks, I tried that. Now, when I try to add the m4a files to the Music Library, gtkpod crashes:

> *** buffer overflow detected ***: gtkpod - terminated
gtkpod: buffer overflow attack in function <unknown> - terminated

Tim

---

### Post by vexorian on 2012-07-30
Try rhythmbox or Amarok, gtkpod seems very unstable lately.

---

### Post by ron999 on 2012-07-30
> **ratcheer said:**
> ... gtkpod crashes... 
Look here ---> [http://ubuntuforums.org/showthread.php?t=2033751]("http://ubuntuforums.org/showthread.php?t=2033751")

---

