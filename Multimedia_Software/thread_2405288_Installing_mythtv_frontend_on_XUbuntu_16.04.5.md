---
title: "Installing mythtv frontend on XUbuntu 16.04.5"
date: 2018-11-03
forum: Multimedia Software
---

### Post by linuxhippy on 2018-11-03
I have an Apollo Lake Mini PC and am having trouble getting mythbuntu installed on it with the iso.  Apparently I have to use a script called isorespin.sh to get Ubuntu flavoured iso files to work but it doesn't consider the mythbuntu iso to be a flavor??  I don't get it.  I also have mythbuntu 16.04.5 installed as a backend/frontend so I figured I could install XUbuntu 16.04.5 on my Apollo Lake (isorespin did work on the XUbuntu iso files) and then get the needed mythtv frontend packages installed.  I found this article but I'm not sure how current this is:

[https://help.ubuntu.com/community/MythTV/Install/Server/Frontend]("https://help.ubuntu.com/community/MythTV/Install/Server/Frontend")

So is the above link still current or are there other packages I need for a mythtv frontend?

---

### Post by TechnoJunky on 2018-11-04
I went to the Mythbuntu site and they have this there for you to add the repo, no script required.

To add the MythTV Updates repo

sudo add-apt-repository ppa:mythbuntu/<Repo Name>
sudo apt-get update

---

### Post by linuxhippy on 2018-11-04
Got it working.  I used the isorespin script available to get XUbuntu 16.04.5 installed on my Apollo Lake mini pc.  I found it here and this seems to be the newest revision as an older isorespin script wouldn't work right:

[http://linuxiumcomau.blogspot.com/2018/03/ubuntu-16044-for-intel-atom-and-apollo.html]("http://linuxiumcomau.blogspot.com/2018/03/ubuntu-16044-for-intel-atom-and-apollo.html")

There are dependencies it needs which this explains:

[http://linuxiumcomau.blogspot.com/2017/06/customizing-ubuntu-isos-documentation.html]("http://linuxiumcomau.blogspot.com/2017/06/customizing-ubuntu-isos-documentation.html")

I downloaded the official XUbuntu 16.04.5, checked the sums and then respun and got a file that I installed from USB.  The USB should be FAT32 filesystem.  To get the new iso file on the USB extract it to your home directory and then go in the folder and copy all the files and directories to that USB flash.

So I got XUbuntu installed and then did the apt update and upgrade.  Then installed synaptic.  I noticed in there that there were already a bunch of packages for mythtv.  I picked mythtv-frontend and mythtv-control-centre which also installed the mythbuntu ppa like TechnoJunky suggested.  Then it found the backend when I ran mythtv-frontend.  It seems to not want to setup audio right (I had the same problem on a laptop frontend) until u go into the frontend settings for audio and test your sound.  Alsa has been setting everything up right for years on all my Linux boxes so I think the sound being muted is just a safety thing.  Once I tested audio and heard a hiss it started using my sound "card".

Now I got TV streaming to this mini PC thanks again to Ubuntu!!

---

