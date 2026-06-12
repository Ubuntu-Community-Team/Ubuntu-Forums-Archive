---
title: "Mythexport - no sound"
date: 2012-06-05
forum: Mythbuntu
---

### Post by ThomPont on 2012-06-05
I am having a lot of trouble getting mythexport to work under my fresh Mythbuntu 12.04 install.

First the job didn't even start - solved by manually creating and chmod'ing mythexport.log

Next the RSS pointed to wrong directory - solved by changing the link /var/www/mythexport/video to point directly at the export directory.

Third and fourth remain:

No sound; I get an "Unknown encoder 'libfaac'" error in the log. I have installed medibuntu and libfaac0. What's missing?

Podcast not working; I can't play/download the files using the RSS link. I think it may have to do with the link being wrong. The links are like this:
```
<enclosure length="" url="http://*host-IP*/mythexport/video/TV-2-Desperate_Housewives_86_-Amerikansk_dramaserie_-2012060412.m" type="video/mpeg" />
```
I would expect the file extension "m" to be "m4v" (as in the actual file), but how do I change that?

My backend is running on a 64 bit AMD. Mythexport is reporting version 2.2.4-0ubuntu1 and libfaac0 is version 1.28-0ubuntu2

---

### Post by nickrout on 2012-06-05
what is the script you are using to process the file and does it worlk on the commandline?

---

### Post by nickrout on 2012-06-05
Maybe the solution is here:

[http://www.gossamer-threads.com/lists/mythtv/users/519287](http://www.gossamer-threads.com/lists/mythtv/users/519287)

---

### Post by rhpot1991 on 2012-06-06
Pull the updated configs from here: [http://www.baablogic.net/mythexport/](http://www.baablogic.net/mythexport/)

And make sure you have Medibuntu enabled: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ThomPont on 2012-06-06
Thanks both!

I will check out the new configs - tried the 1.2 yesterday which resulted in no file being created at all, but I can see there is hectic activity going on in that area:)

Regarding medibuntu - I am certain I got the repository activated, but from the error I am getting I suspect libfaac is not available to ffmpeg. Any easy way to check - and repair if my suspicion is correct - I have seen guides on how to compile ffmpeg with libfaac, but since I'm not "do-it-yourself" capable in these matters I hope there is a more user friendly way?

---

### Post by rhpot1991 on 2012-06-06
> **ThomPont said:**
> Thanks both!

I will check out the new configs - tried the 1.2 yesterday which resulted in no file being created at all, but I can see there is hectic activity going on in that area:)

Regarding medibuntu - I am certain I got the repository activated, but from the error I am getting I suspect libfaac is not available to ffmpeg. Any easy way to check - and repair if my suspicion is correct - I have seen guides on how to compile ffmpeg with libfaac, but since I'm not "do-it-yourself" capable in these matters I hope there is a more user friendly way?

Pull again and make sure the config uses avconv and not ffmpeg.  Those updated configs should just work when you have Medibuntu enabled (required for libfaac).

The easiest way to check would be to run:
```
john@ultramagnus:~$ avconv -codecs | grep libfaac
avconv version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
  EA    libfaac         libfaac AAC (Advanced Audio Codec)

```

---

### Post by ThomPont on 2012-06-07
> **rhpot1991 said:**
> Pull again and make sure the config uses avconv and not ffmpeg.  Those updated configs should just work when you have Medibuntu enabled (required for libfaac).

The easiest way to check would be to run:
```
john@ultramagnus:~$ avconv -codecs | grep libfaac
avconv version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
  EA    libfaac         libfaac AAC (Advanced Audio Codec)

```

Pulled new configs. Fixed the missing sound problem, thanks.

However, I'm still not able to stream/download the podcasts due to the weird file extension in the URL reference. I tried changing the extension of the actual file to ".m" and it downloaded alright.

EDIT: Found a line in the daemon that truncated the filename to '63 characters + ext'. Counted the characters of the links - 63 characters incl. '.m'n. I'm not a programmer, but I took the chance and changed 63 to 61 in the script. This seems to do the trick.

Filed bug [https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/1010080](https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/1010080)

---

### Post by Huphup on 2012-06-22
Hello:

I have a fresh install of Mythbuntu 12.04 and am trying without success to get mythexport to work.

First I ran into the mythexport.log permissions bug, but think I have worked around that. Then I ran into the system not finding libfaac, even when I had activated the medibuntu repository. 

When I forced an install of libavcodec-extras-53 from the medibuntu repository, along with the dependency libavutils, I succeeded in having libfaac available:

```
$ avconv -codecs | grep faacavconv 
version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
  EA    libfaac         libfaac AAC (Advanced Audio Codec)
```

But now the script has been uninstalled due to missing dependencies:

```
$ sudo apt-get -f install mythexport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libav-tools : Depends: libavcodec53 (>= 4:0.8.3-0ubuntu0.12.04.1) but it is not going to be installed or
                        libavcodec-extra-53 (>= 4:0.8.3) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
               Depends: libavutil51 (>= 4:0.8.3-0ubuntu0.12.04.1) but it is not going to be installed or
                        libavutil-extra-51 (>= 4:0.8.3) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
 libavdevice53 : Depends: libavcodec53 (>= 4:0.8.3-0ubuntu0.12.04.1) but it is not going to be installed or
                          libavcodec-extra-53 (>= 4:0.8.3) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
                 Depends: libavutil51 (>= 4:0.8.3-0ubuntu0.12.04.1) but it is not going to be installed or
                          libavutil-extra-51 (>= 4:0.8.3) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
 libavfilter2 : Depends: libavcodec53 (>= 4:0.8.3-0ubuntu0.12.04.1) but it is not going to be installed or
                         libavcodec-extra-53 (>= 4:0.8.3) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
                Depends: libavutil51 (>= 4:0.8.3-0ubuntu0.12.04.1) but it is not going to be installed or
                         libavutil-extra-51 (>= 4:0.8.3) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
 libavformat53 : Depends: libavcodec53 (>= 4:0.8.3-0ubuntu0.12.04.1) but it is not going to be installed or
                          libavcodec-extra-53 (>= 4:0.8.3) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
                 Depends: libavutil51 (>= 4:0.8.3-0ubuntu0.12.04.1) but it is not going to be installed or
                          libavutil-extra-51 (>= 4:0.8.3) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
 libpostproc-extra-52 : Depends: libavutil-extra-51 (>= 4:0.8.3ubuntu0.12.04.1) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
 libswscale-extra-2 : Depends: libavutil-extra-51 (>= 4:0.8.3ubuntu0.12.04.1) but 4:0.8.1ubuntu1+medibuntu1 is to be installed
 mythexport : Depends: libavdevice-extra-53 but it is not going to be installed
              Depends: libavformat-extra-53 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Any help in getting both mythexport and faac installed would be appreciated. Thank you!

---

### Post by rhpot1991 on 2012-06-22
That shouldn't be happening, somehow your ubuntu versions are newer than the medibuntu versions and thus causing you issues.  Do you have any PPAs enabled which would contain these, or maybe backports or something?

---

### Post by Huphup on 2012-06-22
> **rhpot1991 said:**
> That shouldn't be happening, somehow your ubuntu versions are newer than the medibuntu versions and thus causing you issues.  Do you have any PPAs enabled which would contain these, or maybe backports or something?

Hi, thanks for replying. This is a new install of Mythbuntu 12.04, the only repositories that I added other than that are (1) the Mythbuntu repositories for bug-fix updates; and (2) Medibuntu as per the instructions on the Medibuntu mythexport configuration page.

By the way, after posting last night, I discovered that mythexport had been uninstalled by something I had done while trying to fix the dependencies. When I used Mythbuntu Control Centre to re-install mythexport, I ended up in the situation I started in, where, avconv does not have libfaac as one of its codecs and the medibuntu version of the libavcodec-extras-53 is at a lower version than the installed version. 

Here's where I'm currently at:

```
$ avconv -codecs | grep libfaac
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3 
$
```

and 

```
~$ apt-cache policy libavcodec-extra-53
libavcodec-extra-53:
  Installed: 4:0.8.3ubuntu0.12.04.1
  Candidate: 4:0.8.3ubuntu0.12.04.1
  Version table:
 *** 4:0.8.3ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     4:0.8.1ubuntu1+medibuntu1 0
        500 http://packages.medibuntu.org/ precise/non-free amd64 Packages
     4:0.8.1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
~$ 

```

I have been going around in circles, so any suggestions cheerfully accepted.

---

### Post by rhpot1991 on 2012-06-22
It looks like the ubuntu version was updated a few days ago, the best thing to do now would be to ask the medibuntu guys if they can rebuild using the same version.

The ubuntu versions don't contain libfaac, hence the issue here.  The other option would be to install the medibuntu version and lock that version so it doesn't update with the newer ubuntu version.

---

### Post by Huphup on 2012-06-22
> It looks like the ubuntu version was updated a few days ago, the best thing to do now would be to ask the medibuntu guys if they can rebuild using the same version.

Ahh, I didn't notice that. Thanks. I will drop a line to Medibuntu and will move on to my other configuration problems now...

Thank you kindly for your help.

---

### Post by Huphup on 2012-07-02
Just to follow up, medibuntu has upgraded their builds and I've got mythexport working fine with sound and everything :D 

(I did run into the log permission and long-file-name bugs, but thanks to the forums and the bug tracker, I could work around those too.)

Thanks for the help.

---

