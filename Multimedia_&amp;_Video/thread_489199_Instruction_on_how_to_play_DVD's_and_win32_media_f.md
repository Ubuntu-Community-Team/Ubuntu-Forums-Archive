---
title: "Instruction on how to play DVD's and win32 media files dapper drake."
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by badboy_24u on 2007-07-01
Note: These instructions would only work on ver. 6.06lts or dapper drake. Never try to use this on other versions such as edgy or feisty as it may break your system. Good luck. :)

Heres how...

First, go to the terminal and type:" sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-main1 libxine-extracodecs" and press enter.

Second, to add win32codecs repositories, type: "echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update" and press enter.

Third, type: "sudo apt-get install w32codecs libdvdcss2".

Last, go to "Add/Remove" and check the "show unsupported applications" and install "Xine movie player" and ones installed, make sure to make Xine your default movie player because totem movie player doesn't fully support  all types of movie files even with the right codecs installed...

Enjoy!

---

### Post by jasonwstone on 2007-07-01
Says it couldn't find gstreamer0.10-pitfdll?

Jason

---

### Post by badboy_24u on 2007-07-02
Don't worry. You just need to enable two repositories.

Open "Synaptic Package Manager" located on (System-Administration-Synaptic Package Manager).

Now, Click the "Settings" located top left of your screen and select "Repositories".

Click the "Add" button on the right screen and just check the "Community Maintained (Universe) and Non-Free (Multiverse)".

Once your done, close the Package Manager and open the terminal and just type: sudo apt-get update. 

Then type: "sudo apt-get install gstreamer0.10-pitfdll".

---

