---
title: "Pitivi output quality horrible"
date: 2010-10-17
forum: Multimedia Software
---

### Post by Wilbefast on 2010-10-17
I've taken a bunch of videos and I'm trying to edit them together with Pitivi. No matter what combination of container and encoder I choose the output quality is just horrible:

[Before Pitivi]("http://i56.tinypic.com/im0whj.png") and [after Pitivi]("http://i52.tinypic.com/21oseaf.png").

This is actually a cropped version (1280x800 -> 1280x720) - I thought it might make a difference to have an input video this same size as the output video (720p) but it doesn't change anything.

Videos were taken with Fraps - I've done a similar video with Pitivi and the output was fine, but this one just doesn't seem to be working :confused:

Any advice?

---

### Post by SpEcIeS on 2010-10-17
Have you tried OpenShot, or Avidemux?

---

### Post by cotcot on 2010-10-17
The quality is not only determined by choosing the encoder or container. Check the bitrate also. You can find the bitrate in the drop down menu when you click "render project", "modify" , "settings" of video codec. The default bitrate for mpeg for example seems low to me.

I am not sure that other editors will give better results with the same settings. They might be better because the default values are different. 

At the end they use nearly all the same encoders through ffmpeg.

---

### Post by SpEcIeS on 2010-10-17
> **cotcot said:**
>  ... Check the bitrate also. ... They might be better because the default values are different. ...  At the end they use nearly all the same encoders through ffmpeg.

These are all very good points. Personally, I have always used Avidemux, but lately I have been playing around with OpenShot. I just fine these more intuitive, however, each to their own.

---

### Post by Wilbefast on 2010-10-18
I'll give those two a try - I'd thought that the problem might be to do with the change in resolution (from 800p to 720p) but cropping the videos down to 720p beforehand doesn't change anything.

Pitivi seems to be adding this black frame around the outside of the video (see image linked in first post) so the resolution is being cut down, even if the output resolution is technically the same. There are also artefacts, and some encoders are just noise. It's strange :(

Anyway, I'll give OpenShot a try - I'll fiddle with the bitrate too...

---

### Post by Wilbefast on 2010-11-10
Too a while to get onto this - euh, let's see:

OpenShot doesn't like FRAPs video either. I'm getting these wierd vertical bars at the bottom of the screen and in any black areas. Possibly this is due to the input being 1280x800 not 720. 
[URL="http://i54.tinypic.com/mrg2aa.png"]
before[/URL]

[after]("http://i56.tinypic.com/afhjr4.png")

The quality is quite disappointing too. 

Avidemux (GTK+) works really well, but is rather difficult to use and not very "powerful". You can't do seem to do as much with it as with the other programs (shortening, rearranging, etc). It's also can't take .ogg files for music (very strange) and .mp3s don't play properly :(

edit: actually that's just the preview - they work fine in the output. oopsies :S

Maybe I can iron out some of these kinks with a bit of work, but if anyone else had this problems it'd make my life easier to know what you did.

Thanks,


William

---

### Post by SpEcIeS on 2010-11-10
If you run Avidemux while using compiz you will get interference and it is usually best to run the QT version as opposed to the GTK+, depending on your system, for better application performance.

If you can tolerate the learning curve, try CinelerraCV. :)

**[http://cinelerra.org/getting_cinelerra.php#ubuntu]("http://cinelerra.org/getting_cinelerra.php#ubuntu")**
```
Ubuntu 10.10 Maverick Meerkat

    There are no packages for Ubuntu 10.10 Maverick.
    To install CinelerraCV you have to compile it from source. You can find detailed instructions on the Cinelerra for Grandma tutorial.

10.04 Lucid Lynx, 9.10 Karmic Koala, 9.04 Jaunty Jackalope, 8.10 Intrepid Ibex

    for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
    (Replace 'YOURVERSION' with 'hardy', 'intrepid', 'jaunty', 'karmic' or 'lucid' depending on your release)

    deb http://akirad.cinelerra.org akirad-YOURVERSION main

        Installation notes:
        - For your convenience you can install a package for detecting your version of Ubuntu, installing akirad repository and keeping it updated.
        Just double click on the link http://akirad.cinelerra.org/pool/addakirad.deb and install it with GDebi Package Installer.
        Alternatively, use one of the following terminal commands:
        wget -q http://akirad.cinelerra.org/pool/addakirad.deb && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
        or
        echo deb http://akirad.cinelerra.org akirad-YOURVERSION main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
        - 3 are the packages available in the akirad repository:

            Comunity Version of Cinelerra

                cinelerra (all computers)
                cinelerra-xt (same of cinelerra, but with ssse3 enabled that gives about 20% more performance on recent intel cpus)

            Utility

                cinelerra-swtc (extra Shape Wipe Transitions)

        - These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
        - IN EVENT OF UPDATE PROBLEMS RUN THE FOLLOWING TERMINAL COMMAND:
        for i in sv cv cv-gl sv-gl cv-smp sv-smp; do sudo apt-get --force-yes --assume-yes remove cinelerra$i libquicktime$i libmpeg3$i libguicast$i; done && sudo apt-get install cinelerra
        - Please, report any package bug to akir4d at gmail dot com 


```

---

### Post by Wilbefast on 2010-11-10
I'm using 10.04 so should be okay ;-)

For me the important thing is to have an output video that is more or less the same quality as the input, and the ability to cut resize and reassemble clips together. Avidemux only seems able to take one video and append another...

---

