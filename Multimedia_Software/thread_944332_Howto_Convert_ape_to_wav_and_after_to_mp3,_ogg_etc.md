---
title: "Howto Convert ape to wav and after to mp3, ogg etc.."
date: 2008-10-11
forum: Multimedia Software
---

### Post by zeld on 2008-10-11
Today i've try to convert my *.ape audio format into ogg, but with sound converter i've get some error :S i dont know why!!! but i wanted at all cost convert these files!!! After some research with google, i've get some thread that talking about "monkeys-audio" aka "moc" converter!!! i've try to search this on ubuntu official repository, but this not exist :| and then???? i remain with this format file????? NOOOOO!!! IT'S DEATH!!! AHAHHA ok.... seeking always with google, i've found "monkeys-audio" package on debian testing multimedia repository...but i dont want install a debian binary package, because i've not a debian, but i've ubuntu...and is a little different!!! Ok! i search the debian source package and compile it for my machine!!! and this it work good!!! now  and here i post my howto!! Follow this:

#first one add this line to your sources.list:

```

#Debian multimedia
deb-src http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia testing main
```

#Install the key for access to this repository:

```
wget http://www.debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb
dpkg -i debian-multimedia-keyring_2007.02.14_all.deb
```


#Then create a tmp_src_compile directory on  your home, create and install moc package!

```

apt-get update

mkdir tmp_src_compile
cd tmp_src_compile
apt-get source monkeys-audio

cd monkeys-audio*

debian/rules binary

cd ..

dpkg -i libmac*.deb
dpkg -i monkeys-audio*.deb

```

#Convert a file *.ape to *.wav with this command:

```
mac file.ape file.wav -d
```

Convert wav to ogg, mp3 or other file format with sound converter!
Enjoy!
Good look!! 

zeld

---

### Post by edgarde on 2009-03-07
Installing the key seems to be failing on this one.
```
~$ wget http://www.debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb

Resolving www.debian-multimedia.org... 91.121.86.213
Connecting to www.debian-multimedia.org|91.121.86.213|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb [following]
--08:05:43--  http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb
           => `debian-multimedia-keyring_2007.02.14_all.deb'
Resolving ftp.sunet.se... 194.71.11.69
Connecting to ftp.sunet.se|194.71.11.69|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:05:44 ERROR 404: Not Found.
```
apt-get subsequently fails. I'm not sure this would work with the key installed.```
~$ apt-get source monkeys-audio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/mirrors.ecology.uni-kiel.de_debian_debian-multimedia_dists_testing_main_source_Sources - open (2 No such file or directory)
```Damn dirty [FONT="monospace"].APE[/FONT]'s.

---

