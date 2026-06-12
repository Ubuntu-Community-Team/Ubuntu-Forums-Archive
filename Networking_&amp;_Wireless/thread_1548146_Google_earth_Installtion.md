---
title: "Google earth Installtion"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by gpdas on 2010-08-07
Hi all,  I am trying to install Google Earth through Synaptic Package Manager. After click on 'Apply' it shows every thing OK. But I am not getting Google Earth in Applications--Internet menu. I am using 10.04 Pl help.

---

### Post by Revolutionary101 on 2010-08-07
Did you install the "googleearth" package or did you install a variant of it such as "googleearth-data" or "googleearth-package"?

---

### Post by gpdas on 2010-08-09
I installed googleearth-package from synaptic package manager and version is 0.5.7 .
The googleearth icon came in Applications--> Internet menu after restart but when I click on it, it is not opening. It just initializes and exits within 1 to 2 seconds.

---

### Post by ronnielsen1 on 2010-08-09
I have google earth installed but I didn't have googleearth-package installed so I read the instructions
> This utility makes it possible to build your own personal Debian
package of Google Earth. The packaging itself is Free Software, but
the Google Earth program is governed by the copyright holder (Google),
so you may be limited as to what you can do with the resulting
package (i.e. no redistribution, etc). This package will simply help
you create the package--it is your responsibility to use the resulting
package responsibly.

Google Earth's homepage is located at <http://earth.google.com/>.


It's not hard to install from their web site

[http://earth.google.com/intl/en/download-earth.html](http://earth.google.com/intl/en/download-earth.html)

Download from their website. It should give you a package named GoogleEarthLinux.bin

After downloading, open a terminal and navigate to where your download is

chmod +x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin

---

### Post by goosem on 2010-08-09
> **ronnielsen1 said:**
> I have google earth installed but I didn't have googleearth-package installed so I read the instructions


It's not hard to install from their web site

[http://earth.google.com/intl/en/download-earth.html](http://earth.google.com/intl/en/download-earth.html)

Download from their website. It should give you a package named GoogleEarthLinux.bin

After downloading, open a terminal and navigate to where your download is

chmod +x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin

Sorry to ask what might be a simple question, but how do you open a terminal _and_ navigate to where the downloaded file is? I opened a terminal and pasted in the text you listed but just get the reply that it cannot find the downloaded file. The file is, in fact, in the Downloads Folder. Can some kind person explain what I am doing wrong. Regards.

---

### Post by gpdas on 2010-08-09
In the terminal type pwd    It will show the current directory.
Then use cd command to change to the desired directory. for example
cd /your name/Downloads

---

### Post by goosem on 2010-08-09
Thanks for your quick response, unfortunately it reports "No such file or directory". I suspect I am still doing something wrong. Regards.

---

### Post by ronnielsen1 on 2010-08-09
Are you typing in /home/gdpas/Downloads with a capital D? or cd /your name/Downloads

---

### Post by goosem on 2010-08-09
I've typed cd /mike/Downloads which results in"no such file or directory". I also tried cd /home/mike/Downloads from which the response is "Downloads$". I don't understand what this means. Regards

---

### Post by ronnielsen1 on 2010-08-09
OK, Mike, it sounds like you're in the downloads folder if the cursor change. NOW, you can enter the commands

chmod +x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin

or to be more precise

cd /home/mike/Downloads

(Press enter - The cursor will change to reflect that you're in the Downloads folder)
Then type in the following commands followed by pressing the enter button

chmod +x GoogleEarthLinux.bin


sudo ./GoogleEarthLinux.bin

---

### Post by Revolutionary101 on 2010-08-09
> **goosem said:**
> I've typed cd /mike/Downloads which results in"no such file or directory". I also tried cd /home/mike/Downloads from which the response is "Downloads$". I don't understand what this means. Regards

Or if the command line isn't for you, just go to this website [here]("http://packages.medibuntu.org/lucid/googleearth.html") and download the .deb file for your architecture.

---

### Post by ronnielsen1 on 2010-08-09
I didn't know they had a deb out there

---

### Post by Revolutionary101 on 2010-08-09
> **ronnielsen1 said:**
> I didn't know they had a deb out there

Yes they do, it comes from the Medibuntu repositories:

[www.medibuntu.org](www.medibuntu.org)

I don't think it is from Google or the Offical Ubuntu repositories, but it works.

I'm glad I could share my knowledge.

---

### Post by ronnielsen1 on 2010-08-09
Only thing with the deb is I got errors from a new install of beta Ubuntu 10.10 and had to do a sudo apt-get -f install (which worked)

---

### Post by Revolutionary101 on 2010-08-09
Well the link to the .deb file I gave you was for 10.04. I don't know if that has anything to do with the problems you are having.

---

### Post by goosem on 2010-08-10
Thank you, that worked. Regards.

---

### Post by old farmer on 2010-09-03
I had problems installing as well, but I went to the earth google site to get help, and the work around was a redirect to this page:
[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)

Just offering another way
cheers  ):P
Jeffrey

---

