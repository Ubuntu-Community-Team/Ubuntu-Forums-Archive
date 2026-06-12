---
title: "HowTo-Capture a Realplayer Video Stream Using Mplayer"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by Sabot on 2007-04-22
Requirements:
Mplayer - Download with Synaptic
w32codecs - Download with Synaptic after you add Medibuntu repositories

Process:
I will use Democracy Now as an example site.

1. Go to web page that has a Realplayer stream link on it.
```

http://www.democracynow.org/streampage.pl
```

2. Click on the  link that should start a Realplayer stream. In this example the link is "Watch entire show - broadband or dialup"

3. Choose to save to disk the link. It will save some file to your desktop. fjdo9omg is the name of the file in this example.

4. Open the file with a text editor.  You will find in the file a URL that looks something like this:

```
rtsp://rxn-rbn-sea01.rbn.com/farm/*/demnow/demnow/demand/2007/april/video/dnB20070420a.rm
```

5. Open a terminal and enter the code below.  Replace the URL Here and the File Name Here with ones of your choice. Press Enter and Mplayer will save the Realplayer stream to your Home Folder with the file name you choose.  It does this in real time.

```
mplayer -dumpstream -dumpfile "File Name Here.rm" "URL Here"

```

Here is the code for our example Democracy Now Stream

```
mplayer -dumpstream -dumpfile "democracy.rm" "rtsp://rxn-rbn-sea01.rbn.com/farm/*/demnow/demnow/demand/2007/april/video/dnB20070420a.rm"

```

Tip:  You can watch the stream live with another instance of Mplayer or Realplayer just by opening the file that your saving.

---

### Post by khughitt on 2007-06-01
Works great! Thanks! Now I just need to figure out how to convert it a different format like xvid..

---

### Post by khughitt on 2007-06-09
Following-up,- I found [a way]("http://gentoo-wiki.com/TIP_MEncoder_Tips_and_Tricks") to take the streams downloaded in .rm format and convert them to other formats:

First, save the stream using mplayer:
```

mplayer -dumpstream -dumpfile "output.rm" "rtsp://sourcestream"

```

Next, use mencode, convert to a different format.
```

mencoder output.rm -ovc lavc -oac mp3lame -o newoutput.avi

```

I havn't tried other codecs yet, but I imagine it should work with xvid, etc.

---

