---
title: "trouble getting kdenlive"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by atlfalcons866 on 2007-05-02
hi
i cant get kdenlive to install i do this but nothing happens

jack@jack-desktop:~$ udo apt-get install kdenlive
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
Make sure you have the 'universe' component enabled
bash: udo: command not found
jack@jack-desktop:~$ sudo apt-get install kdenlive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdenlive: Depends: libmlt++0.2.3 (>= 0.2.2) but it is not going to be installed
            Depends: libmlt0.2.3 (>= 0.2.2) but it is not going to be installed
E: Broken packages
jack@jack-desktop:~$

---

### Post by Egils on 2007-05-08
There are download links on the following site for a zip archive containing deb packages for kdenlive, mlt and mlt++:

[http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing#Ubuntu]("http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing#Ubuntu")

They may not be the latest versions but they seem to work fine with fiesty.

Another riskier option would be to add a debian-multimedia.org repository (stable or testing) to your sources list, update apt-get, install kdenlive and dependencies without upgrading any other packages, and then remove the repository from your sources list and update apt-get again. I say riskier because you might end up with some conflicts with packages from the Ubuntu repositories. 

Let me know how you go with either option.

---

