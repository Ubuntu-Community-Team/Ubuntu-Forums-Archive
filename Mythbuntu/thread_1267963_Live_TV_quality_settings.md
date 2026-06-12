---
title: "Live TV quality settings"
date: 2009-09-16
forum: Mythbuntu
---

### Post by getafix35 on 2009-09-16
After installing MythTV and getting it up and running, I am not so happy with the picture quality.
Firstly, I am connecting via HDMI from a 9800GT to a 47"LCD. I know that pq on any LCD especially SD tv, is never going to compare to a plasma screen, but if I connect my STB directly to my TV, the quality is far superior. The picture is not nearly as sharp and quite blocky, even from a distance.
Unfortunately I don't understand most of the settings.
 
So, my question is what do you recommend I could change from the default setup that could positively effect my picture quality?
 
The resolution I am using is 1920x1080 (native res of my tv) at 50Hz.
 
Thanks
Gareth

---

### Post by Slate8 on 2009-09-16
A good way to increase the quality of playback is to choose a better playback profile. See [http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)
Personally I use CPU++. It uses more CPU (duh) but the de-interlacing is outstanding.

Also, you can adjust the bitrate of the recordings by using the High-Quality recording profile. I think it's in the TV settings somewhere. The resulting file size will be a little bigger but far less blocky. As far as I know it should affect live tv too as live telly is essentially a recording.

---

### Post by williammanda on 2009-09-16
I issue could be the tuner. What kind of tuner do you have?
Thanks

---

### Post by getafix35 on 2009-09-16
I use the PVR-500 analogue tuner. We don't have FTA HD here in RSA only through a STB.  [Here]("http://www.hauppauge.com/site/products/data_pvr500mc.html") is a pic of the tuner I have. At this stage I am only connecting via the composite inputs. I want to get that working before trying to coax input.
 
Will look at the other possible changes.
 
THanks for the replies guys. 
 
Cheers
Gareth

---

### Post by williammanda on 2009-09-16
> **getafix35 said:**
> I use the PVR-500 analogue tuner. We don't have FTA HD here in RSA only through a STB.  [Here]("http://www.hauppauge.com/site/products/data_pvr500mc.html") is a pic of the tuner I have. At this stage I am only connecting via the composite inputs. I want to get that working before trying to coax input.
 
Will look at the other possible changes.
 
THanks for the replies guys. 
 
Cheers
Gareth

When I used my PVR-150 the quality was never as good as the tv tuner. Then I found a post that did make it better. From the frontend, I use the classic setup, go setup > tv settings > recording profiles > Transcoders create new profile. Here are a couple of other posts. It looks like the setup has changed alittle since I last used it.

[http://ubuntuforums.org/showpost.php?p=5816918&postcount=3]("http://ubuntuforums.org/showpost.php?p=5816918&postcount=3")

[http://ubuntuforums.org/showpost.php?p=3726635&postcount=4]("http://ubuntuforums.org/showpost.php?p=3726635&postcount=4")

Use one of the profiles or make a new one. If I remember right I got rid of the others. Make sure your video setting in the highest (mpeg).

---

