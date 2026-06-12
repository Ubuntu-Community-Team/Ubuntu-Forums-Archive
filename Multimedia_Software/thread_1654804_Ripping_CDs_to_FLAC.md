---
title: "Ripping CDs to FLAC"
date: 2010-12-28
forum: Multimedia Software
---

### Post by v1rati on 2010-12-28
What is the best program (quality-wise) for ripping CDs to FLAC? I've heard of Grip. However, it isn't in the Ubuntu repos. :(

---

### Post by inobe on 2010-12-28
it's not in the repo because it's no longer supported, there are others, here the ubuntu doc

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

look at grip and it points to alternatives, also have a peek at the howto's

edit: a thread about ripping just below

[http://ubuntuforums.org/showthread.php?t=1654247](http://ubuntuforums.org/showthread.php?t=1654247)

---

### Post by gordintoronto on 2010-12-29
Sound Juicer works for me.

---

### Post by Rodney9 on 2010-12-29
Asunder works for me.

---

### Post by shantiq on 2010-12-29
from your terminal if you fancy that route     ===First create a folder on desktop called newtrax or whatever you want==

==================================================


 with pacpl   (most straightforward of commandline rippers)



```
sudo apt-get install pacpl
```



then



```
pacpl  --outdir ~/Desktop/newtrax --rip all  -t  flac --fcomp 8

```


or for single trax

```
pacpl  --outdir ~/Desktop/newtrax --rip 1,2,3  -t  flac --fcomp 8

```


                                 [SIZE="4"]**or**[/SIZE]

```
sudo apt-get install ripit

```    To install the program ripit



then


```
ripit --outputdir ~/Desktop/newtrax  --playlist 0 -c 2 flac-8 --eject --save

```


if you only want some of the trax   list them   2,3,4


============================================================

**[SIZE="3"]if quality[/SIZE]** is really your main concern use [rubyripper]("http://linuxappfinder.com/package/rubyripper")which is the closest to EAC linux has got so far



you can of course also use EAC under wine     

Both of these programs rip twice and compare the 2 files to make sure rip is perfect




SO a lot of choices:KS:KS:KS

---

### Post by conorsulli on 2011-01-12
RubyRipper :-)

---

### Post by BicyclerBoy on 2011-01-12
My vote is for cmd line prog

abcde
uses cdparanoia

This can generate many output formats at same pass.
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

---

### Post by andrew.46 on 2011-01-15
Hi BicyclerBoy,

> **BicyclerBoy said:**
> My vote is for cmd line prog

abcde
uses cdparanoia

This can generate many output formats at same pass.
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

I still get a warm feeling when someone suggests a page from my site :).

Andrew

---

### Post by shantiq on 2011-01-15
> **BicyclerBoy said:**
> 

This can generate many output formats at same pass.



which is a great bonus


can also be done from [rubyripper]("http://linuxappfinder.com/package/rubyripper")
as can be seen on attached image   tick or untick as many as you wish

---

### Post by nothingspecial on 2011-01-15
> **andrew.46 said:**
> Hi BicyclerBoy,



I still get a warm feeling when someone suggests a page from my site :).

Andrew

I do it often, stay warm :p

---

### Post by cascade9 on 2011-01-15
> **shantiq said:**
> **[SIZE=3]if quality[/SIZE]** is really your main concern use [rubyripper]("http://linuxappfinder.com/package/rubyripper")which is the closest to EAC linux has got so far

you can of course also use EAC under wine     

Both of these programs rip twice and compare the 2 files to make sure rip is perfect


+1 to Rubyripper. Its as good as EAC 'test and copy' in most cases (rubyripper isnt quite as good as EAC in dealing with damaged discs IMO)

---

### Post by SeijiSensei on 2011-01-16
This is an area where KDE has an advantage over GNOME, I think.  If you open an audio CD in the KDE file manager, Dolphin, it automatically provides you the option of extracting individual tracks, or the entire album, into any format for which you have codecs.  You can then rip the CD simply by dragging and dropping tracks from the folder in your preferred format to your hard drive or other storage medium.

---

### Post by shantiq on 2011-01-16
seiji reminded me with his message that there is also a piece of software which is handy for a quick rip



```
 sudo apt-get install sound-juicer

``` or get through synaptic or software centre

---

### Post by oldos2er on 2011-01-16
Grip is still around: [http://nostatic.org/grip/grip-download.shtml](http://nostatic.org/grip/grip-download.shtml)

---

### Post by shantiq on 2011-01-17
yes still around and an easy way to install thanx to rapido is [here]("http://ubuntuforums.org/showpost.php?p=8759491&postcount=25")

---

### Post by shantiq on 2011-01-17
-

---

### Post by shantiq on 2011-01-17
hmm the ppa does not seem to be there anymore-


but this works  **all from rapido's script**


```
wget http://downloads.sourceforge.net/project/grip/grip/3.3.1/grip-3.3.1.tar.gz?use_mirror=superb-dca2
```

then rename file in home folder to grip-3.3.1.tar.gz (it did not automatically in my case)


```
tar -xzvf grip-3.3.1.tar.gz

``````
cd grip-3.3.1
```

# get the dependencies
```
sudo apt-get update

``````
sudo apt-get install libgnomeui-dev libvte-dev libcurl4-openssl-dev
```

# build and install
```
./configure

``````
make
```
```
sudo make install

```
# install other useful libraries   Most probably already have those but if not


```
sudo apt-get install lame flac vorbis-tools
```


then i found it had located itself in    /usr/local/bin   so i went there

```
cd  /usr/local/bin
```   and moved it to /usr/bin  
```

sudo cp /usr/bin 
```

Then go to Applications/sound and video/    and it is there   ** go to config/encode  to set to flac**

---

