---
title: "MythVideo IMDB Search Broken by New IMDB Page Layout"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by ebs16 on 2007-02-20
IMDB rolled out a new site layout today, breaking the "Search IMDB" feature on MythVideo.  I can now successfully pull movie titles and DVD covers, but the director, movie description, and all other information are missing.  Has anyone released a fix for this?

Thanks!

:popcorn:

---

### Post by majoridiot on 2007-02-21
since it was just broken, kick back and allow a little time for the fix.

impatient much?  LOL :D

---

### Post by toorima on 2007-02-25
download [http://svn.mythtv.org/trac/browser/trunk/mythplugins/mythvideo/mythvideo/scripts/imdb.pl?format=raw](http://svn.mythtv.org/trac/browser/trunk/mythplugins/mythvideo/mythvideo/scripts/imdb.pl?format=raw)
and rename it to imdb.pl and copy it over the old one  /usr/share/mythtv/mythvideo/scripts/imdb.pl

Howto do it
make backup
```
sudo cp /usr/share/mythtv/mythvideo/scripts/imdb.pl /usr/share/mythtv/mythvideo/scripts/imdb.pl-orig
```

download file
```
wget http://svn.mythtv.org/trac/browser/trunk/mythplugins/mythvideo/mythvideo/scripts/imdb.pl?format=raw
```

rename file
```
mv imdb.pl\?format\=raw imdb.pl
```

"install" it
```
sudo cp imdb.pl /usr/share/mythtv/mythvideo/scripts/imdb.pl
```

---

### Post by scoultas on 2007-02-26
Thanks - these instructions worked perfectly!

Steve

---

### Post by ebs16 on 2007-02-26
The new script works well. Thanks!

---

### Post by Dubstar_04 on 2007-02-27
Same here worked spot on. Thanks

---

### Post by Morientes on 2007-03-01
How do I get the IMDB scripts to work?
Is it supposed to get the info automatically when I enter a movie folder? Or am I supposed to press some button? I saw that I should press the i button, but this only brings up a menu that allows me to view the file or view plot...I cant seem to get the posters and so on...

What do I do wrong?

---

### Post by toorima on 2007-03-01
Go to Utilities/Setup / Video Manager and press i

---

### Post by Morientes on 2007-03-03
Yeah, I found out that it was in video manger that it could be done.
Would be nice to have the option in the media library though!

---

### Post by peekj on 2007-03-05
Great, this works really well, thanks!

---

### Post by rolnxyz on 2007-03-06
This is weird, I tried the script and it didn't get the **writers**. I had to change line 139 of the file imdb.pl from this:

```
my $data = parseBetween($response, ">Writing credits <a href=\"/wga\">(WGA)</a></h5>", "\n<br/>");
```

To this:

```
my $data = parseBetween($response, ">Writing credits</h5>", "\n<br/>");
```


Otherwise the script would show always an empty string for the writers. 
Anyways, I tried my solution just a couple of times and it worked, maybe I'm missing something, because it seems to work pretty well for the rest of you. 
Please, let me know if I am right so I can report it.

---

### Post by superm1 on 2007-03-07
Once you guy's straighten out which needs to be changed, I'll get this into the feisty package to make sure that feisty mythvideo users don't run into it.

---

### Post by majoridiot on 2007-03-12
toorima's fix: sudo cp imdb.pl /usr/share/mythtv/mythvideo/scripts/imdb.pl worked perfectly the first time for me.

(thanks!) :D

---

### Post by aserpent on 2007-03-16
I'd just like to thank you for this fix.  This has made my use of MythVideo that much more enjoyable and I am grateful.

---

### Post by superm1 on 2007-03-18
Here, I filed a bug about this and should have it fixed in feisty:

[https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/93435](https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/93435)

---

### Post by Jimmy The Clown on 2007-03-20
Rock on! Thanks. Works great.

-JTC

---

### Post by toorima on 2007-04-12
lately I haven't got any info in director and in the painted veil I got no plot, but just run trough the steps again and everything works fine again.
They must have done some updates on imdb.com again.

---

### Post by ebs16 on 2007-04-17
It looks like the Director and Writer fetch broke again.  These imdb.pl modifications seem to fix this issue:

Change LINE 134 to:
```
my $director = parseBetween($response, ">Director:</h5>", "/a><br/>");
```

Change LINE 139 to:
```
my $data = parseBetween($response, ">Writers <a href=\"/wga\">(WGA)</a>:</h5>", "\n<br/>");
```

Hope this helps!

:popcorn:

---

### Post by majoridiot on 2007-04-17
> **ebs16 said:**
> It looks like the Director and Writer fetch broke again.  These imdb.pl modifications seem to fix this issue:

Change LINE 134 to:
```
my $director = parseBetween($response, ">Director:</h5>", "/a><br/>");
```

Change LINE 139 to:
```
my $data = parseBetween($response, ">Writers <a href=\"/wga\">(WGA)</a>:</h5>", "\n<br/>");
```

Hope this helps!



GREAT fix... works like a champ.  Thanks a lot! :D

---

### Post by toorima on 2007-04-17
Or just run trough the steps again, it will give you the latest version of imdb.pl from svn

---

### Post by majoridiot on 2007-04-18
the director fetch is still broken for multiple directors... which has been bothering me for awhile.  here is a fix for it
i came up with last night.  it works well, as far as i can tell.

the only hitch is that depending on your resolution and theme, it might run together some info on the manager
screen.  it works fine in the gallery as far as i can tell.

to make the change, replace the **#parse director block**  beginning at line 133 with the following:

```
   # parse director
   # parse first two, if multiple directors
   my $director = parseBetween($response, ">Director:</h5>", "/a><br/>");
   if (!$director) {
      my $data = parseBetween($response, ">Directors:</h5>", "<a class=");
      my $director1 = parseBetween($data, ">", "<");
      $data = parseBetween($data, "a><br/><a", "/a><br/>");
      my $director2 = parseBetween($data, ">", "<");
      $director = "${director1} and ${director2}";
   } else {
   $director = parseBetween($director, ">", "<");
   }
```

i'll submit a patch for this if it works out ok for everyone.  feedback is appreciated...

(except for making fun of my coding... i knew *nothing* about perl when i did this) :razz:

---

### Post by LilYoda on 2007-09-01
Kudos, this worked...

THis thread is linked from mythtvtalk.com :)

---

### Post by Nightwalker07 on 2007-10-24
I came across this thread because I am now having problems with grabbing IMDB data through MythTV. It was working just fine, my whole MythTV installation was working well and then with no obvious reason it seems I can no longer can retrieve the information from IMDB!? Like I said it did work fine before both using the automatic search and manually entering the imdb number, but now nothing. Internet connectivity on the system is still fine, I cant think of anything other that has changed that might break it, so is it on IMDB's end again?

**Anyone else suddenly experiencing problems with IMDB data retrieval again?**

---

### Post by ryansinn on 2008-03-25
yeah IMDB retrieval didn't work for me in 0.20.x and I just upgraded to 0.21.0 and it doesn't work their either :)

---

### Post by majoridiot on 2008-03-25
> **ryansinn said:**
> yeah IMDB retrieval didn't work for me in 0.20.x and I just upgraded to 0.21.0 and it doesn't work their either :)

have you tried running the imdb grabber in a terminal to see what sort of errors it is generating when it fails?  it is working 98% of the time in my .20 
backend and works perfectly in the new mythvideo for a .21 backend i just built.

---

### Post by Kissell on 2008-04-25
hmm...  is this happening again?

mine was working, but now it is doesn't pull plot information.

I've replaced the imdb.pl script as instructed in this post, but it still won't import the plot field of the video metadata.

---

### Post by Kissell on 2008-04-25
Yes, it was happening again...  

Nobody fixed my problem within five minutes, so I gave it a try and it was actually pretty simple to remedy.

here is what imdb.pl looks like:
>    # parse plot
   my $plot = parseBetween($response, ">Plot Outline:</h5> ", "</div>");
   if (!$plot) {
      $plot = parseBetween($response, ">Plot Summary:</h5> ", "</div>");
   }


But, IMDB must have changed their page yesterday, or else the original .pl file in the repository was changed, cause mine was working, and getting the current original file doesn't work anymore.  

The reason it's not working, is the search string is wrong.  There is a space after the </h5>, however, on IMDB pages on the internet today, there is no space, so this search is never executed properly.

new code needs to look like:
>    # parse plot
   my $plot = parseBetween($response, ">Plot Outline:</h5>", "</div>");
   if (!$plot) {
      $plot = parseBetween($response, ">Plot Summary:</h5>", "</div>");
   }


I'll try to attach a working version to this post (you may have to rename it to imdb.pl if the forum prevents attaching script files)

---

### Post by Alcopops on 2008-04-26
Nice piece of detective work! Made the change and the script works again.

Thanks!

---

### Post by jnorth on 2008-04-30
Yet another change possibly - mine stopped working and looking at the source of IMDB now, there is no "Plot Outline:" any more.  I changed the plot section to the following - not sure if that was the proper way to do it but it works for me again.
```
   # parse plot
   my $plot = parseBetween($response, ">Plot:</h5>", "</div>");
   if (!$plot) {
      $plot = parseBetween($response, ">Plot Summary:</h5>", "</div>");
   }

```

---

### Post by Alcopops on 2008-04-30
Cheers jnorth,

Perhaps this thread could be made sticky and then people could use it to stay up to date with the changes they need to make in their script.

Just a thought.

---

### Post by jnorth on 2008-04-30
> **Alcopops said:**
> Cheers jnorth,

Perhaps this thread could be made sticky and then people could use it to stay up to date with the changes they need to make in their script.

Just a thought.
That'd be nice - any mods around that could sticky?

Only reason I found it was after hacking mine to work, I wanted to see if there was a better way to fix it.  My hacking skills - while they work - are usually ugly :)

Edit: I just realized this is an archived thread so it may not be possible - I'm going to try to edit the MythTV wiki though with the updates.

---

### Post by Kissell on 2008-04-30
Yes, I noticed yesterday that the plot ouline is missing on IMDB pages now too...  So it's definately IMDB doing changes.  I only started using this a week ago, and have many movies to do.

I know this is a little off topic, but does anyone have a script I can cron?  When I add a new movie to my movie folder, I'd like a script running like every hour automatically that will pull in the IMDB information for it.  I'd like to forget out this and move on once I pull in the information for my current movies.  But I guess if IMDB makes daily changes, this dream is out.

---

### Post by Alcopops on 2008-05-05
Looks like the script is broken again, this time mythvideo displays the imdb number followed by a segment of code and also fails to parse any information from the website.

---

### Post by Kissell on 2008-05-05
These errors seem to be occuring frequently due to IMDB's frequent changes to their results code, and this perl script importing based on parsing the web page result.

Has anyone tried this instead?
[http://www.imdb.com/interfaces#unix]("http://www.imdb.com/interfaces#unix")

I haven't got around to it yet, but I think it will keep a current copy of the IMDB data locally, and we could potentially query off of that instead.  

The theory is that IMDB changes their display results code often, but the structure of the underlying database is probably fairly static.

---

### Post by Alcopops on 2008-05-05
Sounds good Kissell,

It seems a bit impractical to maintain a local copy of the data though, it would take up a lot of space if poster art was included. I wasn't sure if the website was saying that was necessary or that a cli was available to interrogate the online db. If the former is the case some kind of third party hosting would be better than everyone maintaining a copy of the data locally i would have thought. Not too knowledgeable about these things though so I probably overlooked something crucial here.

Cheers,

---

### Post by usererror on 2008-05-22
> **jnorth said:**
> Yet another change possibly - mine stopped working and looking at the source of IMDB now, there is no "Plot Outline:" any more.  I changed the plot section to the following - not sure if that was the proper way to do it but it works for me again.
```
   # parse plot
   my $plot = parseBetween($response, ">Plot:</h5>", "</div>");
   if (!$plot) {
      $plot = parseBetween($response, ">Plot Summary:</h5>", "</div>");
   }

```

This fix also worked for me, removed the extra space AND the " Outline" and it works great.  Adding this to my own wiki.

---

### Post by jnorth on 2008-06-17
Release date is broken it seems on my modified script, and I can't figure out how to get it working again.  There's a line break in there now and I can't figure out how to get the script to see and parse that for some reason, and I'm no good with sed or any text search and replace tools like that to hack something together.

Ahh well - until someone with a little more insight than I comes along I can do without the release date.

---

