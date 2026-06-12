---
title: "DVD problems w/ new 7.04"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by shimumu on 2007-10-03
I did a reinstall on my System 76 Pangolin Value laptop & installed the System 76 drivers. DVDs will play only on VLC. Totem says I need the codec

I tried to install it by typing

[INDENT]sudo apt-get install libdvdcss2[/INDENT]

but I got the following:

[INDENT]E: Type '“deb' is not known on line 37 in source list /etc/apt/sources.list
E: The list of sources could not be read.[/INDENT]

I also thought Automatix might help, so I followed the instructions I found here: [http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04_p6](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04_p6)  

That didn't work b/c getautomatix.com is not responding.

Please help & thanks

---

### Post by rsambuca on 2007-10-03
You have an error in your sources.list.  Post the output of 

cat /etc/apt/sources.list

---

### Post by rusty0101 on 2007-10-03
I think the problem is that the package is now being maintained in a repository that you either do not have included in your apt-sources, or that may be off line for some reason.

I would look carefully through the /etc/apt/sources.list file to confirm that the syntax for line 37 is correct. This may include verifying that the path given matches the actual path on the server Once you have confirmed that (or reverted to an earlier copy and used the System > Administration > Software Sources tool to add the recommended repository) you will need to do a refresh on the repository (Synaptic or the Software Sources tool will prompt you to do that, or if editing the file by hand use 'apt-get update'.)

Once that is done, you should be able to install the package. You may also want to add the gpg keys for that repository as well, presumably the instructions that provided you with the location for the file has instructions for doing that as well.

The library in question has significant legal concerns for US residents. I do not know if there is an equivalent library available through the commercial repositories. If there is, I would strongly recommend paying the registration and subscription fees to make use of it for US Residents. I believe that appropriate instructions for setting up, installing, and using those libraries should be available there, if the libraries exist.

---

### Post by shimumu on 2007-10-03
I opened up the sources list (I didn't even know how to do that from a command line yet), and one of the sources had quote marks around it. I took them out and I don't have the same error messages. However, I was prompted to reinstall the System 76 drivers, which I did.

I entered

[INDENT]sudo apt-get install libdvdcss2[/INDENT]

and got back

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/INDENT]

Totem now plays only FBI warnings & other frontmatter on DVDs; Kaffeine won't play DVDs at all; VLC does, as before.

I don't know how to add the gpg categories for that repository.

I'm not sure if it's relevant anymore, but here is the output of 

[INDENT]cat /etc/apt/sources.list[/INDENT]

[INDENT]## Ubuntu 7.04 System76 Repositories Listing

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

## System76 Driver Repository
deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./
[/INDENT]

---

### Post by RomeReactor on 2007-10-03
Hi. Is that the complete sources.list? the error you're getting seems to be related to having quotes around the entries for Automatix repositories (read the [comments here]("http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html")). If you still have the Automatix repositories on your sources.list, try opening the file in Gedit:
```
gksudo gedit /etc/apt/sources.list
```
If your Automatix entry reads like this:
```
&#8220;deb http://www.getautomatix.com/apt feisty main&#8221;
```
remove the quotes so it reads like this:
```
deb http://www.getautomatix.com/apt feisty main
```
Now save the file, close Gedit, and update the repository information:
```
sudo apt-get update
```

If you **don't** have the Automatix entries, just run the update.

On a side note: what are you trying to install that you need Automatix? there really is no need for it; if you want to enable DVD playback,[ look here]("http://ubuntuforums.org/showpost.php?p=3399733&postcount=8").

---

