---
title: "Streaming to ps3 AND xbo 360"
date: 2008-09-16
forum: Multimedia Software
---

### Post by t3k on 2008-09-16
I can never seem to get the settings correct to stream to both xbox and ps3. I had fuppes set up properly for xbox 360 but I could not get it to work for my ps3 so I rebuilt it and started over from scratch. This got my box streaming to my ps3 properly but would no longer work with xbox. I set up profiles i believe they're called for each device but same results. I then set up ushare and got it working for my xbox, but once again the ps3 says unsupported data. fuppes is still running and works for the ps3, but the config is quite poorly setup for it and is difficult to navigate. 

What upnp server can support both devices simultaneously and how would I go about setting it up for both?

---

### Post by HangukMiguk on 2008-09-16
for the time being, use ushare.  it's capable of doing both.  there's a decent howto that got me started with it: 

[http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/](http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/)

NOTE: ushare no longer needs to be patched.

there was another server that seemed to be more capable, but i only found it once when i searched, and never got to try it.  but it looked like it was tons more capable than ushare, if I find it, I will let you know.

---

### Post by HangukMiguk on 2008-09-16
Ok, I found the better one.  It's called TwonkyMedia.  It's a "30 day free trial" but if you use the manual install, there is no trial.

[http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/](http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/)

My gripe WAS with ushare is that it wouldn't read ID3 tags from my music files, and would only give my 360 1,000 of my songs.  Twonky does read ID3 tags, reads all my songs.  Not only that, but with ushare, I had to have all my media in one parent directory.  Not with Twonky.  Also, video files that were not playing with ushare work with Twonky, saving me time re-encoding files.

---

### Post by MrWES on 2008-09-16
I used mediatomb with my son's PS3 without issues. We were able to listen to all our music and just about all avi files; including xvid. I believe it's in the repository. You can even run it as a daemon.

Bill

---

### Post by t3k on 2008-09-17
> **MrWES said:**
> I used mediatomb with my son's PS3 without issues. We were able to listen to all our music and just about all avi files; including xvid. I believe it's in the repository. You can even run it as a daemon.

Bill

 Do you know how well it works with xbox 360?

---

### Post by MrWES on 2008-09-17
Hrmm... I haven't personally set one up, but I believe the Xbox is UPnP compatible, so it should work.

Bill

---

### Post by mushroomblue on 2008-10-19
not only does MediaTomb not work with the 360, the developer actively refuses to support the system, because it has a broken UPnP spec.

it's a shame, nothing compares to Windows Media Center on the machine. 

I have two Xbox 360's streaming video from three different machines (two ubuntu boxes running TwonkyVision, and a Vista Machine running Media Center and a TV tuner). nothing else is as good as TwonkyVision for linux. and that's not saying too much.

---

### Post by bearcharger on 2008-10-29
i have been using ushare to stream video to my xbox360 for awhile and haven't had any complaints.  i'm pretty sure i read a post on here that had instructions on setting it up, but it's been awhile so i'm not too sure.  i know there's definitely a guide out there somewhere though.

---

