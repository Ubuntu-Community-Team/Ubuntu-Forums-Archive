---
title: "Openshot 1.3.0 = 1.2.2 ???"
date: 2011-02-17
forum: Multimedia Software
---

### Post by Braveheart1980 on 2011-02-17
I really have no idea,why this is happening!

I did have some problems on the past (see [here](http://openshotusers.com/forum/viewtopic.php?f=11&t=761)) , but now I tried to install the new version of openshot. BUT after I did that, I realized that infact version 1.2.2 was installed instead of 1.3.0!!

I did everything againa and again,but no luck...

Here is what i EXACTLY did (again and again...)

1) ```
george@Laptop:~$ sudo add-apt-repository ppa:jonoomph/openshot-edge
[sudo] password for george: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 0E8CD101D02D5629A7CBC1A4FC0D5CCAEDFBD1F9
gpg: requesting key EDFBD1F9 from hkp server keyserver.ubuntu.com
gpg: key EDFBD1F9: "Launchpad Bleeding-Edge OpenShot PPA" not changed
gpg: &#931;&#965;&#957;&#959;&#955;&#953;&#954;&#972;&#962; &#945;&#961;&#953;&#952;&#956;&#972;&#962; &#960;&#959;&#965; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#940;&#963;&#964;&#951;&#954;&#945;&#957;: 1
gpg:              &#945;&#956;&#949;&#964;&#940;&#946;&#955;&#951;&#964;&#945;: 1
george@Laptop:~$
``` 

I already had the mentioned PPA,but I did that to be sure

2) sudo apt-get update


3) ```
george@Laptop:~$ sudo apt-get install openshot
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#960;&#949;&#961;&#953;&#947;&#961;&#945;&#966;&#942;&#962; &#964;&#951;&#962; &#964;&#961;&#941;&#967;&#959;&#965;&#963;&#945;&#962; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#925;&#917;&#913; &#960;&#945;&#954;&#941;&#964;&#945; &#952;&#945; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#945;&#952;&#959;&#973;&#957;:
  openshot
0 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 1 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 0 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 2 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
&#935;&#961;&#949;&#953;&#940;&#950;&#949;&#964;&#945;&#953; &#957;&#945; &#956;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#969;&#952;&#959;&#973;&#957; 0B/16,5MB &#945;&#960;&#972; &#945;&#961;&#967;&#949;&#943;&#945;.
&#924;&#949;&#964;&#940; &#945;&#960;&#972; &#945;&#965;&#964;&#942; &#964;&#951; &#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945;, &#952;&#945; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#951;&#952;&#959;&#973;&#957; 44,4MB &#967;&#974;&#961;&#959;&#965; &#945;&#960;&#972; &#964;&#959; &#948;&#943;&#963;&#954;&#959;.
&#960;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951;, in file '/var/lib/dpkg/available' near line 45523 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_karmic': invalid character in revision number
&#917;&#960;&#953;&#955;&#959;&#947;&#942; &#960;&#961;&#959;&#951;&#947;&#959;&#973;&#956;&#949;&#957;&#959;&#965; &#945;&#960;&#949;&#960;&#953;&#955;&#949;&#947;&#956;&#941;&#957;&#959;&#965; &#960;&#945;&#954;&#941;&#964;&#959;&#965; openshot.
(&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#946;&#940;&#963;&#951;&#962; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#969;&#957; ... &#960;&#961;&#959;&#962; &#964;&#959; &#960;&#945;&#961;&#972;&#957; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#940;&#952;&#951;&#954;&#945;&#957; 228757 &#945;&#961;&#967;&#949;&#943;&#945; &#954;&#945;&#953; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#953;.)
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#945;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; openshot (&#945;&#960;&#972; .../openshot_1.3.0-maverick1_all.deb) ...
&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#969;&#957; trigger &#947;&#953;&#945; python-gmenu ...
Rebuilding /usr/share/applications/desktop.el_GR.utf8.cache...
&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#969;&#957; trigger &#947;&#953;&#945; desktop-file-utils ...
&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#969;&#957; trigger &#947;&#953;&#945; man-db ...
&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#969;&#957; trigger &#947;&#953;&#945; shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#969;&#957; trigger &#947;&#953;&#945; python-support ...
&#960;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951;, in file '/var/lib/dpkg/available' near line 45523 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_karmic': invalid character in revision number
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; openshot (1.3.0-maverick1) ...
&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#969;&#957; trigger &#947;&#953;&#945; python-support ...
george@Laptop:~$ openshot
--------------------------------
   OpenShot (version 1.2.2)
--------------------------------
Process no longer exists: 30229.  Creating new pid lock file.
on_mnuHistory_toggled called with self.GtkCheckMenuItem
on_nbFiles_switch_page
on_nbFiles_switch_page
state saved
on_frmMain_destroy
george@Laptop:~$ 
```

As you can see openshot is STILL version 1.2.2

I also tried to install it from the deb itself , but nothing changed.....

.....

Any ideas?

PS1 I just have to mention that previously I tried to compile and install the latest alpha version of openshot , from source , so that may have messed up stuff. I just don't know where to look....

PS2 I even downloaded the .deb file from [here]("https://launchpad.net/openshot/1.3/1.3.0"), extracted it in my Temo folder, went to bin subfolder and tried to run openshot but STILL it reports 1.2.2...

```
george@Laptop:~/&#923;&#942;&#968;&#949;&#953;&#962;/openshot_1.3.0-1_all/usr/bin$ ./openshot
--------------------------------
   OpenShot (version 1.2.2)
--------------------------------
Process no longer exists: 31764.
```

---

