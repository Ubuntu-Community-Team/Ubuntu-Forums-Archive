---
title: "VLC plays iTunes songs???"
date: 2010-11-29
forum: Multimedia Software
---

### Post by spydeyrch on 2010-11-29
So, I have been trying to convert my iTunes DRM songs (the $0.99 ones) over from apple's proprietary format to .mp3. I have search for different programs and haven't been too thrilled.

Then by accident, I happened to open one in vlc (on my windows machine) and it played!!! So I thought, well maybe it was the non-drm version. So I purposely bought a song I liked (and didn't have yet) and made sure it was the $.99 version. I tried to play it in windows media player and other media players I had. they were all unsuccessful, stating that they didn't have the correct codecs. But then I opened it in vlc and BAM! it played right away!

So I restarted into my ubuntu 10.04 x64 machine, opened vlc, directed it to my windows music library and BAM! it played!

I was very surprised that it could play!!! I thought that apple's proprietary drm songs were non-playable in other media players???

Is this old news that I am getting excited about for no reason? Am I like way behind the times or something because I was and still am a little surprised/confused.

So then the thought came: itunes can play in wine. At least for purchasing music. I know that syncing doesn't work. But what if I were to purchase songs via itunes and then played them in ubuntu via vlc!!!!???  It should work, right?

I even though about it a little more:

Is there a portable version of vlc for a platform like android? what if I were to purchase music via itunes in wine and then upload the songs to an android phone and play them via the portable vlc? Would it work?

Just some spur-of-the-moment thoughts/ideas.

-Spydey

P.S. I know that there is the ubuntu music store, and amazon, and other music stores that already sell songs in the .mp3 format or other open-source formats. But I have like 30 gigs of music and 300 gigs of movies/tv shows already purchased via itunes. Hence I am trying to find a way to convert them over to a more manageable format or a work around.

I have some windows programs that do it but it takes like twice as long as the movie to convert it so not really very efficient. See what I mean?

---

### Post by Psyael on 2010-11-29
Apple has not sold songs with DRM since April 2009. Songs before they switched you have to pay up to "upgrade" them to DRM-free versions, but songs you bought since April 2009 are DRM-free AAC audio files.

If the song was bought after then, it's probably either the .M4A container or AAC audio codec that is confusing Windows Media Player, which was never very good out of the box until Windows 7. Most players in Ubuntu (Rhythmbox, Totem, Banshee, etc) should not have a problem.

---

### Post by spydeyrch on 2010-11-29
> **Psyael said:**
> Apple has not sold songs with DRM since April 2009. Songs before they switched you have to pay up to "upgrade" them to DRM-free versions, but songs you bought since April 2009 are DRM-free AAC audio files.

If the song was bought after then, it's probably either the .M4A container or AAC audio codec that is confusing Windows Media Player, which was never very good out of the box until Windows 7. Most players in Ubuntu (Rhythmbox, Totem, Banshee, etc) should not have a problem.

Wow, see I was not aware of that. I do remember that they wanted me to upgrade to a non-drm version. As I remember it, there were two version of the songs. the $0.99 DRM version and the $1.29 non-DRM version.

So no more DRM from Apple? that is great!!! That solves my music problem!!

Now for the movie/video/tv show problem. I really don't want to have to wait like 20 days for my system to finish converting them. And I don't have a bad system. AMD Phenom 9950 2.6 GHz oc'd 3.2GHz, 4GB 1066 RAM, 2 x ATI HD 3870 (crossfired), 2.5TB total of storage (1TB, 3 x 500GB).  Granted the software says that it would go 5x faster with a nvidia cuda enabled gpu, but I have ATI HD 3870 cards. So no go there.

Oh well. More research I guess. 

Thanks Psyael for the info.

-Spydey

---

### Post by Psyael on 2010-11-29
Well, there MAY be no DRM. iTunes or VLC could tell you that. iTunes displays special tags for FairPlay, and all DRM-free tracks are encoded at 256kbps. So if VLC is reporting that as a bitrate, it's DRM free. However, I don't think encrypted iTunes downloads will play in anything other than iTunes and QuickTime Player.

Again, they only started selling everything DRM-free in April 2009 as part of the negotiation to sell songs at price points different than .99 (though there's still plenty of .99 songs!)

If you do have encrypted files, you either have to decrypt them through methods that are probably verboten to discuss here; or use a lossy method like burning songs to discs and then re-ripping them, causing a quality hit.

As far as TV shows are concerned, your only option there is decryptions that may or may not be legal where you live, and likely can't be discussed here. This is why I prefer Amazon's VOD, in addition to being cloud based (as in, all your shows are stored on Amazon and streamed, so you don't have to dedicate storage to the shows) it's mostly platform-neutral.

---

### Post by spydeyrch on 2010-11-30
I wasn't even aware that amazon had a VOD offering. :o That is great!! How good is their selection? I hope it isn't too much like netflix cause netflix won't run in linux. 

Thanks again for the info, very helpful!! :D

-Spydey

---

### Post by samkostka on 2012-05-06
For ones that still have DRM, vlc and banshee play them but not rythmbox.  I tried both, rhythmbox had all songs after 09 and banshee had all of them, even ones from itunes 4 way back then.

---

