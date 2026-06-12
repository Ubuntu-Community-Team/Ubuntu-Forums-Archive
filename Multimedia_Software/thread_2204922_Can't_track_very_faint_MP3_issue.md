---
title: "Can't track very faint MP3 issue"
date: 2014-02-11
forum: Multimedia Software
---

### Post by ken0542 on 2014-02-11
G'day there One & All,

    I know that there have been many posts in this forum & elsewhere regarding the lack of MP3 capability. However I think my problem might be a tad out of the ordinary. Or maybe it isn't but my ability to track it down is less than desirable. In either case, I'm here to ask for assistance. 

    I'm running Xubuntu 13.10 (Saucy) which is updated regularly. It's on an old Dell desktop that I pressed into service but I don't think hardware is an issue. I use Parole and VLC as video players and both work fine with sound & picture operating as one would expect. I have Clementine as a music player/manager. My problem is that MP3 files won't play on any player whatsoever. There are no error messages given if started from a terminal. The position slider moves but no sound emits.

    OK, I have just found that there actually IS sound coming out. I have my volume set to absolute maximum and have only just discovered that there is the faintest of faint sounds noticeable in my headphones. If I play a video the noise blasts me out of my seat, but at least 4 MP3 files (that I just tried) do play but there is barely any volume. I just tried an .WMA and it played with no problems. I can't find where my .OGG files went to or I'd try them too. However I think it's fair to say that I have all the needed libraries & MP3 codecs, since the files play even if faintly, it's just that they hate me for some reason.

    Earlier this morning I opened Synaptic, searched for everything with MP3 in the title and reinstalled what I had. There was no difference. I also worked through the fault finding instructions that are in the sticky post at the top of this forum, but nothing made any noticeable difference. 

    If anyone has any suggestions, I'd be more than happy to hear them :)

Thank you for reading,
Ken

---

### Post by Jonor on 2014-02-13
Perhaps their recorded volume levels were inherently too low. Open them with Audacity to see what the tracks look like, there should be lots of lovely big waves for the average mp3  ;)

---

### Post by ken0542 on 2014-02-14
Thanks for the hint there Jonor, I installed Audacity and did as you said. It seems that every one of my MP3s flatlines! How the hell does that happen? They used to work once upon a time, but now when I make a random selection it shows up dead flat with zero amplitude. Some of these files haven't been played in over 12 months. Surely they can't *all* be corrupted, can they? Hmmm... maybe they can. I just downloaded a test mp3 & it worked fine. It looks like my entire MP3 collection may well be knackered. I wonder how that happened...

Thanks for your assistance there mate. Much appreciated.

---

### Post by FakeOutdoorsman on 2014-02-14
Can you provide a sample file?

---

### Post by Bucky Ball on 2014-02-15
If it is showing flatline in Audacity then there is nothing there. And yes, they could all be corrupt. Post a sample file. Can you right click on a file and 'Properties'. Does it show there is actually data there? (How big is the file?)

---

### Post by ken0542 on 2014-05-22
> **Bucky Ball said:**
> If it is showing flatline in Audacity then there is nothing there. And yes, they could all be corrupt. Post a sample file. Can you right click on a file and 'Properties'. Does it show there is actually data there? (How big is the file?)

Sorry not to get back. Believe it or not, I've not played an MP3 file since my last post here. And promptly forgot all about the issue :(

OK got a file with no output at all, which I've attached/[ATTACH]253379[/ATTACH]. Had to archive it as the site doesn't allow MP3s. Not a biggy anyway.

I just had a quick thought (didn't make my head hurt this time). These files may all have in common that they've been registered in iTunes on my VirtualBox installation. Xubuntu is host, with Win 7 as client. I can't see how reading them into iTunes would make any difference, but I also can't think of anything else that they have in common...

Once again, thank you very much for helping. As you've probably worked out, I haven't got much of a clue about it all.

Ken

---

### Post by ken0542 on 2014-05-22
> **FakeOutdoorsman said:**
> Can you provide a sample file?

Thanks for helping there FakeOutdoorsman. FYI I've attached a file to my reply to Bucky Ball. If you have any ideas I'll be glad to hear them.

I appreciate your efforts.

Ken

---

### Post by MartyBuntu on 2014-05-22
There's nothing there. Either the file is corrupt, or you somehow bulk-converted MP3's to some unplayable format.

---

### Post by Bucky Ball on 2014-05-22
My machine does not even recognise that as a music file at all. Gives me the option to open with Squeeze and that's it. In other words, it thinks it is compressed, which for an mp3 would be correct, but I should be getting offered Audacity, VLC or Audacious (which are the music players I have installed) as I would be for any other music file. 

There is something majorly amiss with that file. Even though it has the .mp3 tag on the end, my machine at least doesn't see it as an mp3.

---

### Post by ken0542 on 2014-05-24
Sigh,   thanks Bucky Ball & you too MartyBuntu. Looks like I'll have to replace over half my music collection. Most of the stuff is from my own CD's, but some were downloaded. I can only think that somehow iTunes has done something but I don't see how. I've not run any sort of bulk routine over the collection that would affect so many files. Regardless of that, there's no way to get back the information that was contained in them so replacement it has to be.

Thanks once again to all of you for helping me out.
See ya
Ken

---

### Post by Bucky Ball on 2014-05-24
Just one thing; I noticed it had a .bz2 on the end of that file which IS a compressed file. I extracted it with Squeeze and voila, it gave me an .mp3 of 500nations (545kbs in size), no .bz2, but .mp3 on the end. When I click on it it opens in VLC, but alas, there is no sound. It plays, just no sound. So, not sure what is happening there.

---

### Post by ken0542 on 2014-05-31
No real mystery there BuckyBall. The forum wouldn't allow me to post an MP3 file so I had to choose one of the permitted filetypes. BZ2 is permitted and has a pretty efficient compression algorithm so I use that to get a file that was small enough to allow it as an attachment (there are limits on archive files to). Hence the .bz2 file extension which became .mp3 when you unbzipped it :)

See? Clear as mud!! <LOL>

---

### Post by Bucky Ball on 2014-06-01
lol. Yep. Got ya! ;)

---

