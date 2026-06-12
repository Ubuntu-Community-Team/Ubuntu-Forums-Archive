---
title: "Installing BBC iPlayer Desktop - fails!"
date: 2009-08-13
forum: Multimedia Software
---

### Post by siabost on 2009-08-13
Hi,

I run Kubuntu 9.04 on an AMD Athlon computer & have been struggling unsuccessfully to install the BBC's Desktop iPlayer for downloading programs.

I had no previous versions of Adobe AIR installed.

The "full" install straight from the BBC website failed/froze after the "preparing to install" dialogue.
Then I installed Adobe AIR from Adobe's site. This seems to have worked.
I then retried installing the iPlayer from BBC.co.uk and got further, getting an option to open or save - tried "open" first and nothing seemed to happen, then tried "save" and that downloaded a 1.5MiB BBC iPlayer Desktop (.air) file. On making this executable & double-clicking the Adobe AIR installer fires up for a split second & then crashes. The same thing happens when I start the AIR installer from the menu & select the downloaded file.

Does anyone have any ideas?

Many thanks.

---

### Post by siabost on 2009-08-25
Anyone...?

---

### Post by mick222 on 2009-08-25
had same problem on ubuntu intrepid .
Opened firefox with gksudo from terminal and installed from there.just noticed a fellow Scot Cumbernauld here.
In Kubuntu i think the command is 

> kdesu firefox
Don't use just sudo it will mess up firefox extensions bookmarks etc.

---

### Post by Darles on 2009-09-01
Use get_iplayer instead. 

[http://linuxcentre.net/getiplayer/]("http://linuxcentre.net/getiplayer/")

I've tried with the beebs own iplayer downloader and it's never worked for me either (that's not saying that it won't for you) but get_iplayer has always worked for me. It's a simple terminal based app that downloads the DRM iphone MP4 streams from  iplayer. You can keep them for as long as you want, watch them when you want and it all very quick and easy.

Darles

---

### Post by siabost on 2009-09-06
Thanks mick222,

I tried installing with firefox & root privileges but unfortunately I got the same result as it fails at the same point.
Fellow scot - it's odd, on these forums you're often dealing with folks from all over the world but rarely within your own locality - just a few minutes down the road too.

Darles,

Downloaded Get_iPlayer & it works very well. Used it from the command line first & now via an excellent GUI devised by Mike H. This and other GUI options available at [http://linuxcentre.net/getiplayer/projects-using-get_iplayer/](http://linuxcentre.net/getiplayer/projects-using-get_iplayer/)

I would recommend Get iPlayer - mick222, it's worth a shot if you haven't tried it. It gives you options on quality - some much higher than the standard BBC iPlayer download.

Thanks again :)

---

### Post by mouchero08 on 2009-09-13
i want to also watch bbc iplayer shows but get stuck on
the content dosent seem to be working
try again later.

i'd like to see/know if you guys got watching programs tru Ubuntu
and if possible can you show a noob the way

---

### Post by siabost on 2009-09-17
Hi mouchero08,

To watch BBC iPlayer I think first of all you need to be based in the UK - worth checking.

If you've only just loaded Ubuntu 9.04 for the first time you will need to add Medibuntu to your repositories list. See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) & scroll down to "Adding the Repositories".
Copy the code under "Any Ubuntu Release & Keyring", open a Terminal (Applications -> Accessories -> Terminal) & paste the code into it. Press the Return key - it will ask for your password: enter carefully as it wont show what you are typing.
NOTE: There's more info on the Medibuntu page if you get stuck.

Once this is done open "Synaptic Package Manager" (I'm not at my regular computer & I can't remember which menu it's under). Again you will be asked for your password. When Synaptic opens click "Reload" at top left.

To use BBC iPlayer you will need the latest Adobe Flash plugin (version 10.0.32...or something like that). Search for Flash within the list of programs. It would also be useful to install the Java plugin (currently version 6.... I think.

Install your chosen program from Synaptic by selecting the tick box beside the program name, choossing "install", click "Apply" on the menu bar, OK the list it tells you it's going to install, click "Apply" again & you should see it downloading and installing your program.

All you should need to do now is open or restart your browser (Firefox?)& try BBC iPlayer. NOTE: You need a decent broadband connection speed for iPlayer to work without stopping and starting.

There are other options if your connection speed isn't good enough & these are already mentioned in this thread.

Best of luck.

---

