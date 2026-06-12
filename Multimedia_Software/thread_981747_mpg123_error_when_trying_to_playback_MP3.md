---
title: "mpg123 error when trying to playback MP3"
date: 2008-11-14
forum: Multimedia Software
---

### Post by hurdy on 2008-11-14
Hi Everyone,

Firstly thank you for taking the time to read this post.

I'm having issues with a newly installed version of mpg123.

I built and installed the neccessary files.

In the how to document it said after installation to playback MP3s I need to Change Directory to where my media is stored. This I done.

Then I should only have to type in command line: mpg123 *file name*

After pressing return I get the following error message:

```
mpg123: error while loading shared libraries: libltdl.so.3: cannot open shared object file: No such file or directory
```

Does anyone know what this means please?

Just so you know I'm a newbie to linux.

again many thanks for your time.

Rob.

---

### Post by xc3RnbFO8P on 2008-11-14
In Synaptic Package Manager search:
> **libtool**
check if you got installed:
[B]libtool
libltdl3 
libltdl3-dev[/B]

---

### Post by hurdy on 2008-11-14
hi, thank you for your response.

I type 

```
sudo apt-get install libltdl3
```

And then I get 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libltdl7-dev for regex &#8216;libltdl3-dev&#8217;
libltdl7-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

This means I have it installed.

I do the same for libtool

```
sudo apt-get install libtool
```

and I get the message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

I then do it for libltdl3

```
sudo apt-get install libltdl3
```

and get the following message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libltdl3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libltdl3 has no installation candidate
```


I also searched for the file libltdl.so.3:

```
whereis whereis libltdl.so.3
```

and I get the following:

```
libltdl.so: /usr/lib/libltdl.so.7 /usr/lib/libltdl.so /usr/local/lib/libltdl.so.3 /usr/local/lib/libltdl.so
```

I'm not too sure what this all means if I'm to be honest.

Does this aid you in anyway?

Thank you again for your time and help.

---

### Post by hurdy on 2008-11-14
oh I have a new error now.

when I type:

```
mpg123 *filename*
```

I get the following now:

```
mpg123: error while loading shared libraries: libmpg123.so.0: cannot open shared object file: No such file or directory
```

so then I typed:

```
whereis libmpg123.so.0
```

and got:

```
libmpg123.so: /usr/local/lib/libmpg123.so /usr/local/lib/libmpg123.so.0
```

---

### Post by Zack McCool on 2008-11-14
While it is not likely the newest cutting-edge version, have you tried the version from the repositories?  Even if you decide to use the newer one, installing the repo version first should help out with any dependency issues you may have...

It is in the universe repo...

---

### Post by hurdy on 2008-11-14
ah ha that did it! Thank you ever so much.

I just downloaded and installed an older version. Works a treat.

Many thanks for both of your input. Very helpful.

Thank you.

---

### Post by xc3RnbFO8P on 2008-11-14
delete

---

### Post by Zack McCool on 2008-11-14
no problem!

I generally recommend trying the repos first for most installs.  You might not get the latest version, but you are likely to get a stable version, and it will usually get you the right dependencies, even for newer versions...   ;)

Cheating isn't always bad...   ;)

---

