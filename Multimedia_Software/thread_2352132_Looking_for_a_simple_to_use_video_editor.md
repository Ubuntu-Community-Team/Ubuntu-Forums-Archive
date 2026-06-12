---
title: "Looking for a simple to use video editor"
date: 2017-02-09
forum: Multimedia Software
---

### Post by jacatone on 2017-02-09
I can't seem to find a simple to use video editor like exist in Windows. OpenShot and other timeline editors are terrible. Just looking for something that shows the video file and has a slider for beginning and end of cut. Don't need disolves, titles, flipping logos, etc. Thanks.

---

### Post by thehipho on 2017-02-09
avidemux2 - install the applications from [GetDeb]("http://www.getdeb.net/updates/Ubuntu/16.10/?q=avidemux")

---

### Post by RobGoss on 2017-02-10
Have you tried kdenlive? [https://kdenlive.org/download/](https://kdenlive.org/download/) it's pretty simple to use and gets the job done. I believe it's also in the Ubuntu repositories as well

---

### Post by jacatone on 2017-02-21
These editors are too complicated. In the Windows world there are simple video editors that you just drag and drop a video file into the program, move a beginning and end slider, then select cut. I can't even figure out how to add a file to this Kdenlive program. They're totally unuseable.

---

### Post by Perfect Storm on 2017-02-22
Have you tried Pitivi? It's drag and drop.

---

### Post by RobGoss on 2017-02-22
This is not **Windows** so you can't compare how things work for two totally different operating systems

With a little reading anything can become usable

---

### Post by jacatone on 2017-02-24
I know it's not Windows. I just wish it was as reliable as Windows. Try accessing the file I want to edit in these linux programs using Open or New and it takes me no where. Unbelievable.

---

### Post by marseille2 on 2017-02-25
I've been looking for something to do quick slicing just to slice off a piece here and there ... I saw [Vidcutter]("http://www.omgubuntu.co.uk/2017/01/vidcutter-video-trimming-linux-app") and wanted to take it for a spin but I haven't got around to it yet. Maybe it would interest you? It's cross-platform and uses Python and QT5.

---

### Post by jacatone on 2017-02-28
Thought I'd installed vidcutter using the instructions below but doesn't appear in any menu and doesn't launch from the terminal.

> How To Install VidCutter on Ubuntu 16.04 LTS +

To install VidCutter on Ubuntu 16.04 LTS or later you can add the official VidCutter PPA to your software sources.

To do this, open a new Terminal window and enter:

```
sudo add-apt-repository ppa:ozmartian/apps

sudo apt update && sudo apt install qml-module-qtmultimedia vidcutter
```


Tried Pitivi. That thing makes no sense. I see there's a very small cut icon at the far right but no play, pause, stop buttons anywhere. I think the people who design these appz must intentionally want to frustrate you.

---

### Post by lisati on 2017-02-28
@jacatone: I've added [noparse]> , ```
, 
``` and [/noparse] to help the formatting of your quote.

According to the [website]("http://www.omgubuntu.co.uk/2017/01/vidcutter-video-trimming-linux-app") you quoted, you should be able to access the program from unity dash.

---

### Post by Perfect Storm on 2017-03-01
> **jacatone said:**
> 
Tried Pitivi. That thing makes no sense. I see there's a very small cut icon at the far right but no play, pause, stop buttons anywhere. I think the people who design these appz must intentionally want to frustrate you.

You do that here: marked with red
[img]https://ubuntuforums.org/attachment.php?attachmentid=273935&stc=1&d=1488346862[/img]

---

### Post by yoshii on 2017-03-03
Video editors by their very nature tend to be complex somewhat.   Windows freewares sometimes have fewer feaures, but they aren't necessarily really full video editors.   But 32-bit AVIdeMux for Windows does work just fine in Ubuntu over Wine (assuming Wine is up to date enough, personally I use Wine-devel versions from [http://winehq.org](http://winehq.org) ).   AVIdeMux can be used to trim and join (append) videos as well perform some nice special edits via plugins.  I've been using it for several years.   I find that the XVID / MP4 / HuffYUV / MKV options are the most useful.  Also, you can disable the video track if you want.  It's freeware.

---

