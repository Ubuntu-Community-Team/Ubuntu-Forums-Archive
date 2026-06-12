---
title: "How do I automatically run the Video Manager update?"
date: 2008-01-28
forum: Mythbuntu
---

### Post by jakev383 on 2008-01-28
I like to add videos to my NFS share as I get them, but I really hate having to go into the video manager and scan for the new videos on each of the frontends that I have.  Is there a way to run this as a cron job or anything?
Thanks.

---

### Post by stdPikachu on 2008-01-29
Not that I'm aware of, no. Also something I'd like improving. I don't think there's any cron commands you can use to do it either, save for re-implementing the "scanner" portion of mythvideo in another app.

---

### Post by jakev383 on 2008-01-29
> **stdPikachu said:**
> Not that I'm aware of, no. Also something I'd like improving. I don't think there's any cron commands you can use to do it either, save for re-implementing the "scanner" portion of mythvideo in another app.

If it's a button on a web page, couldn't this be cron'ed using lynx or something to call the button? Just a thought. It would be nice to have though!

---

### Post by stdPikachu on 2008-01-29
If there is a button on the video page I certainly haven't seen it yet (my master backend/apache/mythweb is still gentoo for the time being) but will have a look later.

---

### Post by newlinux on 2008-01-29
I don't remember their being a specific button, but I do seem to remember there being a URL that would run a scan. But if you don't care so much about metadata for your videos you can put mythvideo in "browse" mode where it shows files that haven't been scanned in (and you can play them). This is in the setup menu.

---

### Post by stdPikachu on 2008-01-29
Aye, I've already got it in browse mode, just wish there was a way to automate IMDB lookups (don't really fancy inserting the output from imdb.pl into the DB myself either).

---

### Post by newlinux on 2008-01-29
> **stdPikachu said:**
> Aye, I've already got it in browse mode, just wish there was a way to automate IMDB lookups (don't really fancy inserting the output from imdb.pl into the DB myself either).

For automated IMDB lookups:
[http://www.mythtv.org/pipermail/mythtv-users/2007-September/195918.html](http://www.mythtv.org/pipermail/mythtv-users/2007-September/195918.html)

For RageTV information insertion for TV shows  (requires user intervention to say yes/no to information insertion and requires files to already be in the database - so useful after running the above script for shows not in IMDB):

[http://www.mythtvtalk.com/forum/viewtopic.php?t=7077&postdays=0&postorder=asc&start=0](http://www.mythtvtalk.com/forum/viewtopic.php?t=7077&postdays=0&postorder=asc&start=0)

---

### Post by stdPikachu on 2008-01-29
Cheers for the links, but still a bit of a blind alley. RageTV.com doesn't appear to exist any more (certainly couldn't find any TV information on it) and his web page just gives me a continual "Loading..." spinner. Will give the bulk updater a whirl next time I go on a transcoding binge.

---

### Post by newlinux on 2008-01-29
I just went to the download URL and it works fine for me. I just used the script this morning. haven't used the bulk imdb script, however. The actual site with the data is tvrage.com

---

### Post by stdPikachu on 2008-01-29
D'oh, he said ragetv.com in his blurb. Just tried his site in FF and it worked, another opera-hostile site... stupid thing won't even let me save the tarball URL. Gah! Fecking useless javascript-everything links.

Anyhow, testing it out now.

Bah, it chokes horribly on my filename format (what's with the predeliction for putting dots instead of spaces? Don't understand) and it doesn't seem to want to recurse. There's something usable in there with a bit of wizardry...

---

### Post by newlinux on 2008-01-29
Yeah, once it runs through the files once, it won't change them again (it sets the imdb number to 1 to mark it as having gone through it if you accept the db change). To have it go through the files again you'd have to change the imdb numbers back to 0 (through the database directly or by resetting the metadata in video manager). I had good luck with most of my files. I suppose the code could be altered to work on whatever file format. I chose to bulk rename the files that didn't work for me to a format that did work well using the rename utility.

---

