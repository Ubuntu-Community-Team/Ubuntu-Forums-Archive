---
title: "adobe downloaded, but still not working."
date: 2009-02-18
forum: Multimedia Software
---

### Post by hubcity on 2009-02-18
i've been searching threads for a couple days, and trying all the tips...

i just upgraded to hardy heron, and ff broke...(something about a lost child)  so i downloaded and installed opera 9.6.  i like hulu.  it tells me to download adobe...i click on download, and the package installer tells me i already have it.  but i can't find it anywhere...

multiverse (?) is on and i followed all the steps in the thread at the top of this forum....

i am enjoying ubuntu, but am getting overwhelmed by the technical end of things.  if someone could please just give me a walkthrough...i've read psychocats manual a few times, but i still can't seem to watch hulu.  i'm afraid i'm going to go through all of  this when i try to install realplayer as well...

as i said, ibetter at using the programs than knowing how they work...please be gentle... ;)

---

### Post by hubcity on 2009-02-18
is opera and adobe compatible?  the download says it's for firefox....

---

### Post by binbash on 2009-02-18
If you mean adobe flash , yes it is compatible

---

### Post by Reeman on 2009-02-18
Are you talking about adobe reader or flash? The way I run Opera is without actually installing it. You can download just a straight non installing compressed tar.gz file of Opera and then decompress it directly to your /home folder. That way you can run it directly from within a folder called /home/(yourname)/opera-xxxxx. 

Within the newly created /home/opera directory you will find a folder called plugins and all you have to do is download the non installing flash player from Adobe, decompress it and copy the flashplayer.so file directly to the /home/(yourname)/opera-xxxxxx/usr/lib/opera/plugins folder. 

The reason for doing things this way is that sometimes the complication in not having enough permissions to do things are better completely avoided! Opera will be installed somewhere in /usr and depending on the distro can be a real PITA to configure depending on permissions.

It is fine to run Linux programs directly from your /home directory and sometimes makes configuring them much easier.

I am using the 64 bit stuff but you might have to use the x86 depending on your ubuntu install, so the names of the stuff you see might be different.

In the newly created /home/opera directory there will be an install shell script and a shell script just called opera.sh all you have to do is run the opera.sh and not the install. You can even edit your programs menu to include the opera.sh if you feel adventurous.

To install flashplayer follow the screenshots of how I do it.

---

