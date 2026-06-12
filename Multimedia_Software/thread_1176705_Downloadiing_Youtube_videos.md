---
title: "Downloadiing Youtube videos?"
date: 2009-06-02
forum: Multimedia Software
---

### Post by Sentience on 2009-06-02
How do I do it? I found a few command line based programs that say they can do it, but I didnt see any instructions and dont know how to use them without a GUI. 

Does anyone have some simple instructions for using the command line to rip from a youtube or google video?

---

### Post by khelben1979 on 2009-06-02
Use the Firefox plugin: [media converter]("https://addons.mozilla.org/en-US/firefox/addon/8189").

---

### Post by mcduck on 2009-06-02
> **Sentience said:**
> How do I do it? I found a few command line based programs that say they can do it, but I didnt see any instructions and dont know how to use them without a GUI. 

Does anyone have some simple instructions for using the command line to rip from a youtube or google video?

Just open the video in Firefox, and when it's fully loaded take a look in /tmp. You'll find the video there..

---

### Post by Therion on 2009-06-02
> **khelben1979 said:**
> Use the Firefox plugin: [media converter]("https://addons.mozilla.org/en-US/firefox/addon/8189").
Or the Video Download Helper plugin...

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

---

### Post by steeleyuk on 2009-06-02
Another option is the youtube-dl script.

---

### Post by Sentience on 2009-06-02
> **mcduck said:**
> Just open the video in Firefox, and when it's fully loaded take a look in /tmp. You'll find the video there..

Im a noob. How do I look in /tmp?

> **steeleyuk said:**
> Another option is the youtube-dl script.

Do you have the script? I couldnt find it.



And thank you everyone else for your helpful plug-in suggestions.

---

### Post by marort on 2009-06-02
Sentience,

One way to access '/tmp' is (assuming you are running gnome)

Places &#8594; Computer &#8594; File System &#8594; tmp

Then just copy the 'flash video' file (before you close youtube). 


I used to run MMC (Mobile Media Converter) and it used to work great downloading Youtube videos, but now it gives me a error all the time.
'Could not get the redirect URL. YouTube download algorith is broken'

I am not sure why this is happening but I am glad there are other alternatives.

---

### Post by marort on 2009-06-02
Sentience,

For instructions on how to use the youtube-dl script go to:

[http://www.nuxified.org/blog/download_youtube_video_files_with_youtube_dl](http://www.nuxified.org/blog/download_youtube_video_files_with_youtube_dl)

---

### Post by warchief_ryan on 2009-06-02
I prefer to use AdBlock Plus for firefox, and wget the direct link, open blockable items and the type will be object subrequest.

Ive been able to do this with any website ive been to, not just youtube, if the video is streaming you'll see it in blockable items.

You can hit the youtube HD button also and see the HD vid link appear.

---

### Post by andrew.46 on 2009-06-12
Hi marort,

> **marort said:**
> For instructions on how to use the youtube-dl script go to:
[http://www.nuxified.org/blog/download_youtube_video_files_with_youtube_dl](http://www.nuxified.org/blog/download_youtube_video_files_with_youtube_dl)

and of course the youtube-dl script itself contains usage instructions:

```

andrew@skamandros~$ **[COLOR="Purple"]youtube-dl --help[/COLOR]**
Usage: youtube-dl [options] url...

Options:
  -h, --help            print this help text and exit
  -v, --version         print program version and exit
  -i, --ignore-errors   continue on download errors
  -r L, --rate-limit=L  download rate limit (e.g. 50k or 44.6m)

  Authentication Options:
    -u UN, --username=UN
                        account username
    -p PW, --password=PW
                        account password
    -n, --netrc         use .netrc authentication data

  Video Format Options:
    -f FMT, --format=FMT
                        video format code
    -b, --best-quality  download the best quality video possible
    -m, --mobile-version
                        alias for -f 17
    -d, --high-def      alias for -f 22

  Verbosity / Simulation Options:
    -q, --quiet         activates quiet mode
    -s, --simulate      do not download video
    -g, --get-url       simulate, quiet but print URL
    -e, --get-title     simulate, quiet but print title

  Filesystem Options:
    -t, --title         use title in file name
    -l, --literal       use literal title in file name
    -o TPL, --output=TPL
                        output filename template
    -a F, --batch-file=F
                        file containing URLs to download
    -w, --no-overwrites
                        do not overwrite files
    -c, --continue      resume partially downloaded files

```

Still my favourite youtube downloader :-).

Andrew

---

