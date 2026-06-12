---
title: "Icecast and FLAC - Anyone have an ezstream config file?"
date: 2010-11-26
forum: Multimedia Software
---

### Post by HellesAngel on 2010-11-26
Hello everyone - first post to this board but I've been a long time reader.

On a Ubuntu Server 10.10 install I have the icecast2 server running, with ices2 client.  This appears to be working fine except for one minor problem - all my music is in FLAC format and it seems ices2 won't play this.  

A bit of Googling showed up the ezstream client as being the best choice for streaming FLAC through icecast2, unfortunately I can't find any suitable example configuration files for this transcoding.  

Before I jump in and create something from scratch can anyone offer an example or some help?  My Linux/Ubuntu/XML understanding level is moderate and any help is much appreciated.

---

### Post by nothingspecial on 2010-11-26
If your server is 64bit, you may need to install ia32-libs

---

### Post by HellesAngel on 2010-11-27
Thanks for the reply.  The server is indeed 64 bit but that wasn't really the question.  I'm just after an example xml config file for ezstream to get started.  My initial Googling didn't reveal one.

---

### Post by nothingspecial on 2010-11-27
> **HellesAngel said:**
> Thanks for the reply.  The server is indeed 64 bit but that wasn't really the question.  I'm just after an example xml config file for ezstream to get started.  My initial Googling didn't reveal one.

No problem :D

I have no idea about, nor have ever used  ezstream.

It`s just that the similar software I do use, needs the 32 libs to work with flac files.

:popcorn:

---

### Post by HellesAngel on 2010-11-29
Which software do you use, I'll check it out too.  It may be easier than starting from scratch.  I haven't had time to look again so in principle all options are open.

---

### Post by nothingspecial on 2010-11-29
I use squeezeboxserver, which is free from logitech.

They make money by selling you the hardware, that`s up to you, I have four of the things and they are excellent pieces of kit. But you can use it without the hardware.

```
sudo nano /etc/apt/sources.list
```Put this line at the end
```

deb http://debian.slimdevices.com stable main
```save and close.
```

sudo apt-get update && sudo apt-get install squeezeboxserver ia32-libs     
```Then access it in your browser by typing in the address bar
```

localhost:9000
```Tell it where your music is. While it`s scanning your music, set up the clients on that machine and any other host machines.

First get the dependencies and building tools
```

sudo apt-get install build-essential subversion libasound2-dev libncurses5-dev liblircclient-dev
```Then, for 32bit
```

svn checkout http://squeezeslave.googlecode.com/svn/squeezeslave/trunk/squeezeslave
cd squeezeslave
make -f makefile.linux26-alsa-display realclean
make -f makefile.linux26-alsa-display
```or for 64bit
```

svn checkout http://squeezeslave.googlecode.com/svn/squeezeslave/trunk/squeezeslave
cd squeezeslave
make -f makefile.linux26-i64-alsa-display realclean
make -f makefile.linux26-i64-alsa-display
```Then run squeezeslave on each of the clients like so

```
./bin/squeezeslave -D 192.168.0.3
```changing the ip address to the one you installed squeezeboxserver on.

You navigate the menus with your arrow keys. Or you can control it through the web interface.

Move the squeezeslave/bin/squeezeslave binary into your $PATH or leave it where it is.

Also, as you start each squeezeslave (client) it is a good idea to rename them through the settings in the web interface otherwise as far as the server is concerned they will all be called squeezeslave.

If I haven`t made a typo somewhere here it will be a miracle.

If you don`t want to go about compiling squeezeslave, I`ve read that amarok can use the server. But I have never tried.

---

### Post by nothingspecial on 2010-11-29
Just found a gui client

[http://wiki.slimdevices.com/index.php/SqueezePlay_Build_Instructions](http://wiki.slimdevices.com/index.php/SqueezePlay_Build_Instructions)

The build instructions are included in the package.

Not tried it myself. I will though.

---

### Post by HellesAngel on 2010-11-30
Many thanks for the explanation, it's an interesting idea.  I know the  Squeezeserver and boxes well, I have four of the hardware players and  run the server - your instructions will be useful as I intend to convert  this server to Ubuntu in due course.  

That said I'm not convinced Squeezebox server is ideal for this purpose -  it will be running on an internet visible server and as much as I  admire the Squeezeserver I don't want it that side of my firewall for  security reasons.  The aim of this server is to make my music available  to me while I'm away from home and so the server being attacked is a  constant threat, and I see this in the firewall (IPCOP) logs.

---

### Post by nothingspecial on 2010-11-30
You are probably right:D

I assumed you were doing this over your lan.

I use a different approach, with one of those sansa thingys and a good few sd cards.

They also serve as an extra backup.

I find the squeezeslave useful though. I do have the hardware in my livingroom, kitchen, bedroom and .....(ahem)..... my wife`s dressing room.

But I use squeezeslave in my office and in my kids` bedrooms.

Like having 7 squeezeboxes \\:D/

Glad my snippets may  have been some use though.

cheers

---

