---
title: "how to install skype 4.2 under ubu 64 bit"
date: 2013-07-12
forum: Multimedia Software
---

### Post by Claus7 on 2013-07-12
Hello,

my main problem installing skype 4.2 on maverick 64 bit (and other versions as well) was the following message:
> ./skype: error while loading shared libraries: libQtWebKit.so.4: cannot open shared object file: No such file or directory

and that message was displayed while I was trying to launch skype via the command:
```
./skype
```

I have to add also, that, trying to download any 32-bit version as a deb file for my box did not work either.

So, in order to install the newest version this is what I did:

1) Download the dynamic version of skype from skype website.

2) Untar it at any place you like, yet keep in mind the path.
For this installation purposes the path will be: /home/*your_user_name_here*/Desktop/skype-4.2.0.11

3) Download the libqtwebkit4_2.2.1-1ubuntu4_i386.deb file from here: 
[http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/libqtwebkit4_2.2.1-1ubuntu4_i386.deb.html](http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/libqtwebkit4_2.2.1-1ubuntu4_i386.deb.html)
-have in mind that we are downloading the 32 bit version even if our box is 64 bit
-just click on the download icon on that page link in order to save the deb file to your machine

4) Then open that file with your archive manager (right click -> open with archive manager) and extract from /usr/lib/i386-linux-gnu/
all the files that it has (maybe not all of them are needed, yet it just works) to your skype folder from before

5) Now, in order to start skype type the following command:
```
LD_LIBRARY_PATH=/home/*your_user_name_here*/Desktop/skype-4.2.0.11/:$LD_LIBRARY_PATH /home/*your_user_name_here*/Desktop/skype-4.2.0.11/skype
```

and that's it!

Happy ubuntu-ing,
Regards!

---

### Post by Cavsfan on 2013-07-12
> **Claus7 said:**
> Hello,

my main problem installing skype 4.2 on maverick 64 bit (and other versions as well) was the following message:


and that message was displayed while I was trying to launch skype via the command:
```
./skype
```

I have to add also, that, trying to download any 32-bit version as a deb file for my box did not work either.

So, in order to install the newest version this is what I did:

1) Download the dynamic version of skype from skype website.

2) Untar it at any place you like, yet keep in mind the path.
For this installation purposes the path will be: /home/*your_user_name_here*/Desktop/skype-4.2.0.11

3) Download the libqtwebkit4_2.2.1-1ubuntu4_i386.deb file from here: 
[http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/libqtwebkit4_2.2.1-1ubuntu4_i386.deb.html](http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/libqtwebkit4_2.2.1-1ubuntu4_i386.deb.html)
-have in mind that we are downloading the 32 bit version even if our box is 64 bit
-just click on the download icon on that page link in order to save the deb file to your machine

4) Then open that file with your archive manager (right click -> open with archive manager) and extract from /usr/lib/i386-linux-gnu/
all the files that it has (maybe not all of them are needed, yet it just works) to your skype folder from before

5) Now, in order to start skype type the following command:
```
LD_LIBRARY_PATH=/home/*your_user_name_here*/Desktop/skype-4.2.0.11/:$LD_LIBRARY_PATH /home/*your_user_name_here*/Desktop/skype-4.2.0.11/skype
```

and that's it!

Happy ubuntu-ing,
Regards!

Maverick reached EOL on April 10, 2012.

Here is some info about Skype on Raring Ringtail 13.04 [http://ubuntuforums.org/showthread.php?t=2139202](http://ubuntuforums.org/showthread.php?t=2139202)

---

