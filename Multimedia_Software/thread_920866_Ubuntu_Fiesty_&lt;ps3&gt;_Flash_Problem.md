---
title: "Ubuntu Fiesty &lt;ps3&gt; Flash Problem"
date: 2008-09-15
forum: Multimedia Software
---

### Post by Krashex on 2008-09-15
Alright well, Im fairly new to the whole linux swing of things. I am currently runing Ubuntu Feisty on my ps3. Everything has gone smoothly with the OS so far except for Adobe Flash. Ive read thru I ddont know how many threads now trying to figure what the problem is and still to no avail I cant get flash. If someone could help that would be amazing at this point.

 qoute: *** IMPORTANT NOTICE ***
The fix for this plugin has been released (let's hope that it will last and adobe won't change the md5sum again)
From the menu:
System -> Administration -> Software sources -> be sure than you have selected the "main", "universe", "restricted" and multiverse".
Then go to the Updates tab -> check "security", "updates" and "proposed"
Now "Close" and "Reload".

after that, do this in the terminal:
sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

*** IMPORTANT NOTICE no.2 ***
For all of you that *STILL* complain, which repositories do you use?
Check if your repositories are up to date: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
Otherwise, try switching to "Download from" -> "Main server" (at system -> administration -> software sources)
Close and Reload.

Then do this in terminal:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get remove -y --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

If the above don't work, please post your Ubuntu version release and apt-cache policy flashplugin-nonfree info, it will be easier to track down.

-----------------------------------------------

Ran thru that whole thing, step by step and still nothing.... let me give ya the output I get when I do sudo apt-get install flashplugin-nonfree

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
----------------------------------------------------------

Any Ideas???? thank you for your time and I look foward to getting some of your input on the matter.

---

