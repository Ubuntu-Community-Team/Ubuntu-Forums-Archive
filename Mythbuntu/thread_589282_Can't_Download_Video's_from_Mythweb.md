---
title: "Can't Download Video's from Mythweb"
date: 2007-10-24
forum: Mythbuntu
---

### Post by BladeBC on 2007-10-24
Hi everyone, just a random question about a problem I'm having with my Mythbuntu install recently.  I've noticed that I'm unable to access any of my recorded shows through Mythweb if I use my external IP address.  If I log into Mythweb with my internal address, it works fine.  The message that I receive when I can't download videos is "Firefox doesn't know how to open this address because the protocol (myth) isn't associated with anything"

It did the exact same thing to me once before and just randomly went away, but now that it's back again I was wondering if anyone might have any suggestions about how I can track down what's causing it.

Thanks in advance.

---

### Post by superm1 on 2007-10-24
> **BladeBC said:**
> Hi everyone, just a random question about a problem I'm having with my Mythbuntu install recently.  I've noticed that I'm unable to access any of my recorded shows through Mythweb if I use my external IP address.  If I log into Mythweb with my internal address, it works fine.  The message that I receive when I can't download videos is "Firefox doesn't know how to open this address because the protocol (myth) isn't associated with anything"

It did the exact same thing to me once before and just randomly went away, but now that it's back again I was wondering if anyone might have any suggestions about how I can track down what's causing it.

Thanks in advance.

This is because mythweb detects what kind of machine you connect from.  If you connect from a windows machine, you need dsmyth installed to add a myth:// protocol handler.  This behavior can however be overridden.

---

### Post by BladeBC on 2007-10-24
I've used dsmyth, but that doesn't quite solve my problem.  I don't care about being able to stream.  What I want to do is to download the files to my computer.  Normally, I could just click the tv show link and it would download for me.  Now, it says it doesn't know how to handle the link.  However, like I said, it does work when I use the internal IP but not the external IP.  What part of the configuration could be making this happen?

---

### Post by superm1 on 2007-10-24
Go to 

[http://MACHINE/mythweb/settings/mythweb](http://MACHINE/mythweb/settings/mythweb)

You can modify the behavior here.

---

### Post by BladeBC on 2007-10-24
What should the correct settings be?

As I said, it currently works when I use the local IP address...why would the external IP address make it behave any differently?  This is accessing Mythweb with the same computer, so it's extremely strange.  I think it goes beyond how it's interpreting my Windows computer, because if that was the case it wouldn't work when I used the internal or external IP's.

Thanks again.

---

### Post by andy-roo on 2007-10-26
I believe this is one of the kinks I was trying to work out as well.  Hopefully some of this might help...

One thing I found is the symbolic links in "/usr/share/mythtv/mythweb/data" were broken.  Mythweb uses these for links to videos, music, etc.  They should be set to go to your media folders in "/var/lib/mythtv".  

Another problem for me was the mythweb links to the videos were being generated improperly by the PHP page "/usr/share/mythtv/mythweb/modules/video/handler.php"  More specifically on line 180 the variable assignment was not getting the correct filepath resulting in the broken links. For me the broken links resulted in an error page saying "An unknown module was specified" and this was on any system I tried to access mythweb.

I discovered that the links to the videos were all haphazard because the previously mentioned variable in handler.php
Messed up link:
"http://10.0.2.5/mythweb/myth:%5C%5C%5CMyMythBackend%5Cvideos%5CMovies_local/Aviator.mp4"
Whereas the link should've been like this...
"http://10.0.2.5/mythweb/data/video/Movies/Aviator.mp4"
You can see where the symbolic links do their job by comparing the real filepath to mythwebs link.
The actual filepath to the file is:
"/var/lib/mythtv/videos/Movies/Aviator.mp4"

Maybe you could try to find the correct url to one of your videos, like above, and see what happens.

Strangely, I discovered recently that after upgrading from 7.10rc to 7.10 the video links in mythweb were magically fixed.

I found out about handler.php from this wiki article.  It may some good additional info as well.
[http://www.mythtv.org/wiki/index.php/Play_Recordings_On_Windows_From_MythWeb](http://www.mythtv.org/wiki/index.php/Play_Recordings_On_Windows_From_MythWeb)

---

### Post by Akriss on 2007-10-27
This is how I set it up, and it works.

1.	Set a Samba share of the mythtv\recordings directory (I believe the default directory is /var/lib/mythtv/recordings) 

2.	In the mythweb page ([http://what.ever.addy.is/mythweb/settings/mythweb](http://what.ever.addy.is/mythweb/settings/mythweb)) in the option box &#8220;Video URL:&#8221; enter &#8220; file://my-mythtv-comp-name/my-samba-share-name/ &#8220; (basically the name you see when connecting to your mythtv box from windows.)

Hope that makes sense.

I can right click the recordings and "save as". works like a charm.

---

### Post by superm1 on 2007-10-28
> **Akriss said:**
> This is how I set it up, and it works.

1.    Set a Samba share of the mythtv\recordings directory (I believe the default directory is /var/lib/mythtv/recordings) 

2.    In the mythweb page ([http://what.ever.addy.is/mythweb/settings/mythweb](http://what.ever.addy.is/mythweb/settings/mythweb)) in the option box “Video URL:” enter “ file://my-mythtv-comp-name/my-samba-share-name/ “ (basically the name you see when connecting to your mythtv box from windows.)

Hope that makes sense.

I can right click the recordings and "save as". works like a charm.
Now mind you, out of the box, mythbuntu sets up said samba share :)

---

### Post by TheQuank on 2008-01-22
I'm tying to do the same thing, download from mythweb as uppose to sream.  To fix mine I modified added windows to the list of operating systems under the function video_url in /var/www/mythweb/includes/utils.php

here is the code snipit before modificaiton:

    function video_url($show) {
    // Global override?
        $video_url = setting('WebVideo_URL');
        if ($video_url)
            return $video_url.str_replace('%2F', '/', rawurlencode(basename($show->filename)));
    // Mac and Linux just get a link to the streaming module
      **  if (preg_match('/\b(?:linux|macintosh|mac\s+os\s*x)\b/i', $_SERVER['HTTP_USER_AGENT'])) **
            return root."pl/stream/$show->chanid/$show->recstartts";
    // Windows likely gets a myth:// url -- grab the master host and port
        global $Master_Host, $Master_Port;
    // Is either the browser xor the master in an rfc 1918 zone?
        if (preg_match('/^(?:10|192\.168|172\.(?:1[6-9]|2[0-9]|3[0-6]))\./', $Master_Host)
                xor preg_match('/^(?:10|192\.168|172\.(?:1[6-9]|2[0-9]|3[0-6]))\./', $_SERVER['REMOTE_ADDR'])) {
            return root."pl/stream/$show->chanid/$show->recstartts";
        }


Now, just add windows to the preg_match so it looks like this: if (preg_match('/\b(?:linux|**windows**|macintosh|mac\s+os\s*x)\b/i',

see if that helps any!!

---

