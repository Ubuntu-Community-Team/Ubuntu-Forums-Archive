---
title: "Foobnix!"
date: 2016-06-18
forum: Multimedia Software
---

### Post by Janos_Sandor on 2016-06-18
Hello! 
Before - I'll mention the obvious - I have only seldomly used Linux and have started using Ubuntu only during the past week, so a pre-excuse regarding the (most likely) inherent wretched cretinism of this question is somewhat appropriate.
I want to install Foobnix, since it's the closest thing to foobar2000 in Linux (I don't want to run foobar through wine as it's reasonably pointless), but the terminal command says that the package is outdated, and when trying to install the .deb files, it doesn't work at all.
I would appreciate any help on this issue.

---

### Post by howefield on 2016-06-18
Hello Janos_Sandor and welcome to the forum.

What version of Ubuntu have you installed ?

Also it is usually better to copy/post the exact terminal input and output to better help others to help you,  phrases like "it doesn't work at all" aren't of much use, usually :)

---

### Post by Janos_Sandor on 2016-06-18
Ubuntu 16.04 LTS 
I installed it in Romanian and the terminal input is also in Romanian
```
sudo apt-get install foobnix
Citire liste de pachete... Terminat
Se construie&#537;te arborele de dependen&#539;&#259;       
Se citesc informa&#539;iile de stare... Terminat
[B]Pachetul foobnix nu este disponibil, dar este men&#539;ionat de c&#259;tre alt pachet.
Aceasta ar putea însemna c&#259; pachetul lipse&#537;te, s-a învechit, sau
este disponibil numai din alt&#259; surs&#259;
```

Which translates as ** the foobnix package is unavailable, but is mentioned by another package. This could mean that the package is missing, is outdated, or is only available from another source.** 

Also, from the previous terminal command:

```
W: The repository 'http://ppa.launchpad.net/foobnix-team/foobnix-player/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/foobnix-team/foobnix-player/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/foobnix-team/foobnix-player/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
```

---

### Post by shantiq on 2016-06-18
Janos you could also use [clementine]("https://www.clementine-player.org/") as an excellent library player

[>>  install]("https://www.clementine-player.org/downloads")


```
sudo add-apt-repository ppa:me-davidsansome/clementine
sudo apt-get update
sudo apt-get install clementine
```



=================

If you must really have foobnix; which is really a basic version of clementine


I just installed it from [here]("http://ubuntuhandbook.org/index.php/2013/12/install-foonix-foobar2000-like-ubuntu-linux/") using

```
sudo add-apt-repository ppa:foobnix-team/foobnix-player
sudo apt-get update
sudo apt-get install foobnix
```


I just tried it in 14.04;   if you are in 16.04   you may need to tell software sources by doing this:

in terminal  >>```
  software-properties-gtk
```

then click on other software find 2 foobnix line and change distribution to "trusty"
which is previous LTS

Then reload and foobnix will then work

but really **try Clementine first **i would advise

---

### Post by howefield on 2016-06-18
> **Janos_Sandor said:**
> Which translates [B]as the foobnix package is unavailable, but is mentioned by another package. This could mean that the package is missing, is outdated, or is only available from another source.

The ppa that you are using does not have a repository for Xenial (or Wily for that matter) so basically you are querying a non existent repository, hence the "package is missing" message. How did you try to install the deb package ?

PS. I second the praise for clementine :)

---

### Post by Janos_Sandor on 2016-06-18
Doesn't work now either after changing from trusted.

Does clementine support last.fm, ripping to various formats (including the dreaded 320 kbps mp3 from CD) and tagging?
If it does, that settles it.

---

### Post by Adam_GUI on 2016-06-18
As of last week, Clementine wasn't reporting to last.fm for me.
However, AmaroK is very similar and reports to last.fm just fine; including "Love track" from player functions.

It doesn't support ripping though.
For that, I'd recommend installing LAME and asunder.

---

### Post by shantiq on 2016-06-18
> **Janos_Sandor said:**
> Doesn't work now either after changing from trusted.

Does clementine support last.fm, ripping to various formats (including the dreaded 320 kbps mp3 from CD) and tagging?
If it does, that settles it.



hmmm  did you install it with

```
sudo add-apt-repository ppa:foobnix-team/foobnix-player
sudo apt-get update
sudo apt-get install foobnix
```


Janos  ?   coz I have just tested it in 16.04  now  and it works fine with instructions above



as regards Last Fm it is in Clementine but you need to log in   so i cannot tell you as not personally a member

---

### Post by vasa1 on 2016-06-18
> **Janos_Sandor said:**
> Ubuntu 16.04 LTS 
I installed it in Romanian and the terminal input is also in Romanian
...
If you want stuff to be automatically translated into English, just prefix your command with "LANG=C " including the space but excluding the quotes. So, instead of
```
sudo apt-get install foobnix
``` you'd use```
LANG=C sudo apt-get install foobnix
```

---

