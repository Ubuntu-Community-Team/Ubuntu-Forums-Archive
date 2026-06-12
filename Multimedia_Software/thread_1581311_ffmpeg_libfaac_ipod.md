---
title: "ffmpeg libfaac ipod"
date: 2010-09-24
forum: Multimedia Software
---

### Post by hundred1906 on 2010-09-24
I nearly gave up on finding out how to prepare a video for transcription onto an iphone and got close to buying the Xilisoft utility to run under WINE. Frankly the problem with ffmpeg, winff and libfaac just seemed too daunting. If you don't know what the problem is with libfaac then what I am writing here will be of no interest. The Ubuntu documentation page on the subject of ipod video conversion is not exactly a model of clarity for me of few beans. However I found the howto instructions on this forum at [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) and stepping through these was simple enough because they made clear which version should be used for the Ubuntu version you have.

After going through all the steps I (re)installed WinFF because I really do not have time to get to grips with all the FFMPEG options through the command line.

Running WinFF it came up straight away with the error that it could not find FFPlay. This is or was a known fault (winff 56) and the way round it was to use the Edit button/Preferences/Linux to set the location for the executables for both FFPlay and FFmpeg. I found the location for mine in the /home directory by using the file search facility in Nautilus. There is reference to this error on the forums but I found that a recommended fix ([http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286502](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286502)) did not work for me.

Complicated but so far so good. I have converted a video and transferred it onto the iphone.

---

### Post by FakeOutdoorsman on 2010-09-24
> **hundred1906 said:**
> The Ubuntu documentation page on the subject of ipod video conversion is not exactly a model of clarity for me of few beans.
That documentation is terribly out of date and would be be more useful and less confusing if it was deleted (or even better if it was updated), in my opinion.

> **hundred1906 said:**
> However I found the howto instructions on this forum at [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) and stepping through these was simple enough because they made clear which version should be used for the Ubuntu version you have.
There is an iPod command line example on that guide that should work with an iPhone.  Admittedly, I haven't tested it though, because I lack any iDevices.

---

### Post by Cpierce on 2010-09-24
Try adding Getdeb [http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install) , make sure you pick the right Ubuntu version, update,  then go to Ubuntu Software Center and install the GUI version of Handbrake. Then install the Ipod/Iphone utilities from here [http://packages.ubuntu.com/lucid/libimobiledevice-utils](http://packages.ubuntu.com/lucid/libimobiledevice-utils)  . 

With Handbrake you can convert video to a pre-made Iphone format and save in your home folder. With the utilities, the Iphone will show up in your home folder when plugged in and you can just cut/paste your new video on your iphone. 

Hope that helps

---

### Post by Cpierce on 2010-09-24
By the way, you may want to go to Software center and install "Ubuntu restricted extras" which has all kinds of good stuff.

---

### Post by hundred1906 on 2010-09-28
Thanks for the replies.

Sorry to Cpierce but actioning your advice was difficult which is a great pity because it looked as though it would generate a really good outcome. The getdeb site was not available (at least to my Chrome Browser) except via a Google archive. The instruction on the page to do a manual install using "deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps" failed and I never made it through to the instruction "Add the repository GPG key, open a terminal window and type: ....", not that I would have known what a GPG key actually is.

Interestingly I did not know that I had Ubuntu Software Centre installed or even what it was. Now I know it is at the bottom of the Applications Menu and is aiming to replace Synaptic and other stuff.

---

### Post by Cpierce on 2010-09-28
I just checked the GetDeb site and it is down now for some reason. I would check back later and see if it is back up. Or see if you can find Handbrake deb package somewhere else on the internet. Make sure you get the GUI version and not the command-line version. It really is a great little program and geared toward Iphone/Itouch.

Sorry you had problems with the site.

---

### Post by Cpierce on 2010-09-29
GetDeb site is back up. Select 10.04 or 9.10 from the drop down box at the top of the page and then click on the highlighted "getdeb" in step one to download the deb package. Then run "sudo apt-get update" in terminal. Handbrake should then be available in the software center.

---

