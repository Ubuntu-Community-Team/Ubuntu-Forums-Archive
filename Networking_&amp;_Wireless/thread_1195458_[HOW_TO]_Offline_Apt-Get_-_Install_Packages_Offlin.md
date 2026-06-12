---
title: "[HOW TO] Offline Apt-Get - Install Packages Offline [HOW TO]"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by pyromanic123boom on 2009-06-23
Hey,

When I come to a cumulative discovery over some time, I think that it might be helpful to other people. Especially when it took me so long to really make this workable, then I think it may help people. 

So if you've got a older desktop or laptop running ubuntu, and you are always so pissed when you want to install a *simple* application or program, and you have to go through **all** the dependencies, well... you know what it's like. "I just want to open a damn terminal and type 'sudo apt-get application-to-install' but I have to go to the ubuntu website and download..." Or, "Where did I save that script to generate html links that I can download with firefox...??" 

**[SIZE="4"]Step 1 - Computer w/ internet[/SIZE]**
* I'll assume you're running Firefox. Install the downthemall addon here: [https://addons.mozilla.org/en-US/firefox/addon/201]("https://addons.mozilla.org/en-US/firefox/addon/201") and restart Firefox.

* Go to [http://labs.fajran.web.id/p/apt-web/index.php]("http://labs.fajran.web.id/p/apt-web/index.php"). This link was a genuine lucky find. 

* Type in the name of the package you want to install. (If you don't exactly know the right package name, try testing it in your terminal). It will generate the links to download the '.deb' packages.

* On the Firefox menu bar, click **Tools --> Downthemall Tools --> Downthemall.** Create a folder with the name of your package and select it for the download. Then in the fast-filter selection, type '.deb'. (That's w/o the quotes, duhh). Click start and wait for it to finish. 

* Once they're finished downloading, transfer the downloaded directory to a flash drive and take it to your internet-less computer.

**[SIZE="4"]Step 2 - Computer w/o internet[/SIZE]**
* Insert flash, and transfer the directory over.

* Open a terminal, change to that directory

cd /directory/here

* Now bulk-install all the deb packages at once

sudo dpkg -i ./*.deb

* Tada.

**Problems**

You might have to individually install the packages graphically instead.

The website doesn't always pick up every package, so sometimes you'll still have to go the ubuntu website. But this solution works almost all the time (for me).

---

