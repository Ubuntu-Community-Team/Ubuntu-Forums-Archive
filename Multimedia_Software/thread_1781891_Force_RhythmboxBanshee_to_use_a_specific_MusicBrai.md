---
title: "Force Rhythmbox/Banshee to use a specific MusicBrainz"
date: 2011-06-14
forum: Multimedia Software
---

### Post by superarthur on 2011-06-14
I put the CD in, and neither of the application can fetch the CD info. I thought maybe there isn't a MusicBrainz entry for my CD. However, when I searched on MusicBrainz, my CD did come up. Is there a way to force the application to use a specific entry? Or is there another way arond it (other than typing everything track by track)?

Thanks,
Arthur

---

### Post by dreadmo on 2011-06-14
This is a well-known problem, still not fixed as far as I know. See this thread: [http://ubuntuforums.org/showthread.php?t=1766447](http://ubuntuforums.org/showthread.php?t=1766447) .

---

### Post by mc4man on 2011-06-14
It's been fixed in banshee though don't know if it's in a ppa yet.
(or maybe thinking of other way to fix?

Did so here on 11.10 (banshee 2.10) by re-building using these simple changes

```
--- banshee-2.1.0.orig/src/Extensions/Banshee.AudioCd/Banshee.AudioCd/AudioCdDiscModel.cs
+++ banshee-2.1.0/src/Extensions/Banshee.AudioCd/Banshee.AudioCd/AudioCdDiscModel.cs
@@ -123,10 +123,15 @@ namespace Banshee.AudioCd
 
                 OnMetadataQueryStarted (mb_disc);
 
-                Release release = Release.Query (mb_disc).PerfectMatch ();
+                Release release = Release.Query (mb_disc).First ();
+
+		if (release == null || release.Score < 100) {
+			OnMetadataQueryFinished (false);
+ 			return;
+ 		}
 
                 var tracks = release.GetTracks ();
-                if (release == null || tracks.Count != Count) {
+                if (tracks.Count != Count) {
                     OnMetadataQueryFinished (false);
                     return;
                 }
```

---

### Post by clarkNerd on 2011-07-15
In Banshee, this has been fixed now, but only after version 2.1.0.  If you really care to look into the details, the change was committed on [2011-05-28]("http://git.gnome.org/browse/banshee/commit/?id=ee467bdcf9fe97ed161deef3c5108d2bf5f54db5") but the 2.1.0 branch was created on [2011-05-12]("http://git.gnome.org/browse/banshee/tag/?id=2.1.0").

If you are really itching to get this working again, here are the steps you have to follow: (**Warning, this is the daily repo so you will get lots of update notifications and there is a higher risk of bug introduction.**)

> 
[FONT="Courier New"]
sudo add-apt-repository ppa:banshee-team/banshee-daily
sudo apt-get update
sudo apt-get upgrade
[/FONT]


---

