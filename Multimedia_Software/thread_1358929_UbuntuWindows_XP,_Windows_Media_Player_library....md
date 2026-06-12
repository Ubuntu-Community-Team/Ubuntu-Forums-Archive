---
title: "Ubuntu/Windows XP, Windows Media Player library..."
date: 2009-12-19
forum: Multimedia Software
---

### Post by vyco10 on 2009-12-19
I didn't really know how to phrase the title of this thread. I'm having an issue I don't really know how to diagnose. I have Ubuntu and Windows XP dual-booting off my desktop, with Ubuntu being the first OS installed. I have it this way because I like having Windows around for some things that either I can't do in Linux or some things that are just done better in Windows. Anyway, on to the issue...

For some reason Windows Media Player's library has become screwed up and I think it may have something to do with how Ubuntu is handling my audio files. Where WMP could play everything in my My Music folder... it can't now. And what's strange is that there are a number of folders showing up as doubles in the My Music folder now. For example, there are two identical Alice In Chains directories. Now, if I'm in Ubuntu I can see everything fine and play everything fine, so I don't understand what's going on.

I realize this forum is for help with Ubuntu related issues, but since I'm thinking it probably has something to with Ubuntu I'd say it fits here. Bottom line: I just want to be able to listen to my music regardless of which OS I'm working in.

Thanks.

---

### Post by michael37 on 2009-12-19
> **vyco10 said:**
> I didn't really know how to phrase the title of this thread. I'm having an issue I don't really know how to diagnose. I have Ubuntu and Windows XP dual-booting off my desktop, with Ubuntu being the first OS installed. I have it this way because I like having Windows around for some things that either I can't do in Linux or some things that are just done better in Windows. Anyway, on to the issue...

For some reason Windows Media Player's library has become screwed up and I think it may have something to do with how Ubuntu is handling my audio files. Where WMP could play everything in my My Music folder... it can't now. And what's strange is that there are a number of folders showing up as doubles in the My Music folder now. For example, there are two identical Alice In Chains directories. Now, if I'm in Ubuntu I can see everything fine and play everything fine, so I don't understand what's going on.

I realize this forum is for help with Ubuntu related issues, but since I'm thinking it probably has something to with Ubuntu I'd say it fits here. Bottom line: I just want to be able to listen to my music regardless of which OS I'm working in.

Thanks.

I would run windows checkdisk on the windows partition just to make sure.

---

### Post by Pauly BC on 2009-12-19
I had a similar but much worse experience sharing files between Ubuntu and Windows. Where you have experienced file duplication I had significant file losses. Ubuntu and Windows do not interface very nicely when sharing files on a Windows boot drive; it has to do with the way Windows handles the page file. I recommend you set up a partition from which neither OS boots and store your shared media files on that partition.

If that's not the case get back to us with more details and we can offer other advice.

---

### Post by vyco10 on 2009-12-19
> **Pauly BC said:**
> I had a similar but much worse experience sharing files between Ubuntu and Windows. Where you have experienced file duplication I had significant file losses. Ubuntu and Windows do not interface very nicely when sharing files on a Windows boot drive; it has to do with the way Windows handles the page file. I recommend you set up a partition from which neither OS boots and store your shared media files on that partition.

If that's not the case get back to us with more details and we can offer other advice.

Well, the audio files are actually on a separate hard drive than the drive Ubuntu/Windows is installed on. There wouldn't have been enough drive space otherwise.

The reason I thought of the duplicate directories was because I remember a while back when I was playing around with Songbird to see if it would fit me better than Rythmbox. For whatever reason Songbird saw all of these duplicate files. I went into Songbird's interface somewhere and got rid of the duplicate files. It didn't have any affect on the files in Windows, though, so I don't think that has anything to do with what I've got going on now.

I've thought of uninstalling Windows Media Player. I also ran up on this tutorial that says to delete the db file that WMP uses, but I went to where they said the file would be... and it wasn't there. In fact, it wasn't anywhere. :confused:

It's just a weird thing. First time I've ever seen this. I know there's always reinstalling Windows... but I REALLY can't stress how much I *don't* want to do that.

---

### Post by vyco10 on 2009-12-19
Bump

---

