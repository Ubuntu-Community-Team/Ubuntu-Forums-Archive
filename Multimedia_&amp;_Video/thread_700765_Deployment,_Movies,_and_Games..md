---
title: "Deployment, Movies, and Games."
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by einnar on 2008-02-18
I'm deploying soon with the Army, and am looking at taking a laptop with a dual boot win/linux setup. I'll need the win for compatibility with a lot of the army software, but am setting up a dual boot for entertainment "in my free time".

My goal is to get something on there like MAME (xmame), but also have the ability to copy as much of my DVD collection onto an external 1TB mybook I recently got as a gift. I know how to do the games.. the DVDs are stumping me a bit, as my previous attempts have left me with either a decent copy, or something resembling a godzilla movie. (offset sound)

My question is this : 

MythTV? From what I've read, it'll allow games like I'm referring to, and it has a copy/catalog of dvd's capability.

Is this overkill? Is there a best recommendation that someone can offer? I'm comfortable using linux, and am not put off by having to fiddle around to get something to work, or by xfce, gnome, or KDE. I have no favorite yet. (I know.. heretic. ;) )

Thanks for the assistance!

---

### Post by xzero1 on 2008-02-18
You could rip the dvds to your drive without re-encoding them. Most dvd player software will be able to play the movies and you should have no sound issues. Using a 8-5Gb ballpark estimate per dvd should allow 125 to 200 dvds on your drive. This would also save a lot of time since you wont have to re-encode  to another format.

Good luck on your deployment!

---

### Post by einnar on 2008-02-19
Thanks for the response xzero1.
What method are you using to rip them?

---

### Post by xzero1 on 2008-02-19
Sorry, I've never actually used Linux ripping tools, but I've heard of acidrip and dvd::rip. They can be found via synaptic. In windows, try dvdshrink or smartripper. I would try each and see which is faster since you have to do a lot of ripping. This link should help you out:
[http://www.doom9.org/index.html?/sr.htm]("http://www.doom9.org/index.html?/sr.htm")

---

### Post by einnar on 2008-02-19
Thanks much.
I tried one of them, and got the offset sound. I'll try the other, and see what I get.
And you're right.. I have a lot of cycles to burn here in the near future.

Any other software that anyone would like to recommend would be welcome too. :) If encoding times are about the same, I'd prefer a smaller format for the file. The more I can take with me, the better.

For the record, I own every disk I am looking to put on hard drive. I just can't take them with me in that format for space considerations. I won't be sharing this out in any way, shape, or form that would break any law that I'm aware of. This is for personal viewing while deployed. If I share a move with friends, it'll be with me there, on my machine, and not burning them and handing them out. I'm not looking for something that will let me do that.

Thanks!

---

### Post by xzero1 on 2008-02-20
Something is wrong here. There should be no sound issues because you should be playing the original dvd files -- only from the hard drive with the encryption removed. What format is the file you played? The dvd itself contains video and sound in .vob files. If your ripper gives another format then you are probably already transcribing the files. Try and play the dvd itself and see if you have any sound issues. Try a different dvd player: vlc,mplayer,movie player etc. If you need more space it will cost you more time to re-encode -- possibly a lot more time if you don't have a fast processor.

---

### Post by einnar on 2008-02-20
They were being transcoded on the fly from the DVD. To break it down, I did the following : 

 - made a script that copies the dvd files to the HD when I place it in the drive. (Creates a directory, copies the files, names it after the title, then ejects the disk when done. About 15 mins a DVD to copy)
- queued up those directory files in acidrip and configured it according to directions I found in one of your links. (codecs, pass count, etc.)


The directory files I copied from the DVD play fine in a variety of players, I just have to make a playlist of the appropriate files if that's what I go with. First time I did that, I accidentally put one out of order. :oops:

I'll let you know how the ripping with acidrip to a smaller size works tonight or tomorrow.


The machine I'm encoding on is a 2GHX athalon X2 (64 bit) with a 7800gt evga video card, 2GB memory, on a Gigabyte GA-K8N Pro SLI mobo. Stock (non-64 bit) ubuntu install, with mediabuntu extras (codecs basically) and restricted drivers. (nvidia)

Thanks again.

---

### Post by xzero1 on 2008-02-20
Sounds good. Once you get your sync issues down, you could probably run two different encodes
per cpu with continuous ripping. This will be more efficient than running a single encode multithreaded. Depending on how much compression you want multipass may not be necessary. I would also consider using the latest x.264 codec which seems superior in compression/quality. Only problem is you may have to compile some source for that one. Btw, you can play at least some single pass encodes as they are being encoded  -- just give it a little head start and then play the file. This works great for quality testing different encoding parameters.

Glad to help.

---

### Post by einnar on 2008-02-20
I did do the testing of the stream as it was being encoded.

Ended up using lavc, and the movies are coming out great. About 5-600 MB per, and it's going pretty fast with the method I detailed above.

When I'm home, I keep feeding it DVDs and add each copied directory to the acidrip queue, then run that when I'm at work or sleeping. I like how acidrip lets me export the queue, and basically schedule it too.

Once again, that link to doom9 was gold. Thanks again. :)

---

