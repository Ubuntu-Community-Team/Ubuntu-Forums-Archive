---
title: "Package: Rosegarden4 1.2.3 with DSSI support."
date: 2006-04-19
forum: Multimedia &amp; Video
---

### Post by fdoving on 2006-04-19
Hi, 

I've made a Rosegarden4 1.2.3 package, with DSSI support.
Hope you guys will help me test and give me feedback.

The package is buildt for Dapper / i386. 
You can get the package from my dapper repository.

```

deb http://ubuntu.lnix.net/dapper/ ./

```


- Frode

---

### Post by dolson on 2006-04-19
Thanks for your work on this. You should upload it to REVU to get feedback and get it into Ubuntu. Or alternately, get it into debian Sid by contacting the debian multimedia dev mailing list.

---

### Post by fdoving on 2006-04-19
I will upload to revu. But i'm waiting for the dssi sync from debian.

- Frode

---

### Post by rytmisk on 2006-05-12
Works like a charm! Thank you!!

Anyone know why the packages from willem engen doesn't show up? 
([http://willem.engen.nl/debian/](http://willem.engen.nl/debian/)) Your dssi packages come up fine, but I would really like the qsynth, hexter and so forth.

Best
Ketil Thorgersen

---

### Post by 3saul on 2006-06-12
Can someone please point me in the direction of this rosegarden 1.2.3 package....it's no longer at this address...

Thanks

---

### Post by SoftGround on 2006-06-15
[QUOTE=3saul]Can someone please point me in the direction of this rosegarden 1.2.3 package....it's no longer at this address...
Thanks[/QUOTE]

I pointed my browser at [http://ubuntu.lnix.net/dapper/ ]("http://ubuntu.lnix.net/dapper/")and had no problem downloading the deb.  

However when I put 
```
deb http://ubuntu.lnix.net/dapper/ ./
```
into my sources.list I got errors getting Packages from the server.
It said connection broken, but not sure why.  
I can see the Packages files in the browser and all the other repositiries worked OK.

So you should be able to get the deb file and install it manually, but then you will have the usual dependency mess.  You may be able to use one of the local repositry tricks to get round this. e.g.
Put it in a folder on its own and do
```
dpkg-scanpackages . /dev/null > Packages
```
and then point sources.list at the folder.

SG

---

### Post by fdoving on 2006-06-15
I rebuildt the Packages file. Now it works for me:
```

Get:1 http://ubuntu.lnix.net ./ Packages [2699B]

```
sources.list line:
```

deb http://ubuntu.lnix.net/dapper/ ./

```

- Frode

---

### Post by dolson on 2006-06-15
dssi is in Dapper now.

---

### Post by SoftGround on 2006-06-16
Still getting a problem with ubuntu.lnix.net, 

```
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Ign http://ubuntu.lnix.net ./ Release.gpg
Ign http://ubuntu.lnix.net ./ Release
Get:3 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:4 http://archive.ubuntu.com dapper Release [34.8kB]
Ign http://ubuntu.lnix.net ./ Packages
Err http://ubuntu.lnix.net ./ Packages
  Error reading from server. Remote end closed connection [IP: 192.85.50.87 80]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Failed to fetch http://ubuntu.lnix.net/dapper/./Packages.gz  Error reading from server. Remote end closed connection [IP: 192.85.50.87 80]
Fetched 65.7kB in 3s (19.6kB/s)
Reading package lists...
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I can do wget on the same Packages.gz and there is no problem.

Dolson - does that mean I can use an official repository to get this or are you just referring to the dssi package.

---

### Post by dolson on 2006-06-17
dssi (and plugins like fluidsynth and hexter) are in Dapper. Rosegarden with dssi support is not there, and would have been hard to get in since dssi wasn't added to Dapper until the day (or second day) before Dapper went final. That is not enough time, especially since we were WELL past feature freeze, which was four months ago.

---

### Post by oedipuss on 2006-06-18
Thanks so much for this <3

---

### Post by fdoving on 2006-06-18
[QUOTE=SoftGround]Still getting a problem with ubuntu.lnix.net, 

```
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Ign http://ubuntu.lnix.net ./ Release.gpg
Ign http://ubuntu.lnix.net ./ Release
Get:3 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:4 http://archive.ubuntu.com dapper Release [34.8kB]
Ign http://ubuntu.lnix.net ./ Packages
Err http://ubuntu.lnix.net ./ Packages
  Error reading from server. Remote end closed connection [IP: 192.85.50.87 80]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Failed to fetch http://ubuntu.lnix.net/dapper/./Packages.gz  Error reading from server. Remote end closed connection [IP: 192.85.50.87 80]
Fetched 65.7kB in 3s (19.6kB/s)
Reading package lists...
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I can do wget on the same Packages.gz and there is no problem.

Dolson - does that mean I can use an official repository to get this or are you just referring to the dssi package.[/QUOTE]


Looks like you're using a proxy. As ubuntu.lnix.net is 81.26.52.3 not 
 192.85.50.87.

Seems to be a proxy problem.

- Frode

---

### Post by dolson on 2006-06-18
You could try just downloading the deb, then double-click it, it should open in gdebi I think, and let you install it.

---

### Post by SoftGround on 2006-06-18
Thanks everyone, it does seem to be a proxy problem, my proxy must be getting upset about something to do with apt-get and your address, but I have no idea what.  However it works all other ways.

If you follow my other posts elsewhere you will see I am trying to download using the Live CD at work as I only have dialup at home.  I was hoping to be able to download all the dependencies in one go using a synaptic generated script, following an apt-get update.

I am still in the early stages of proving things before I do the install.  I had installed DeMudi, but realised I needed Rosegarden 1.2.3 to work with the installed version of lilypond, I had other problems with DeMudi as to get everything on the CD lots of useful system things were missing (like printing).

With Ubuntu I feel I can get better support in fixing issues, and there seem to be lots of other people solving the same problems but with different packages across the forums.

I would be interested in an add on UbuntuStudio CD along the lines of UbuntuPlus which had most of the current packages and their dependencies on it.  e.g RG 1.2.3, Lilypond, notedit, audacity.

Im not sure about the RT kernel yet as I have a fast machine and value the stability of Dapper.

Regards and Thanks

SoftGround

---

