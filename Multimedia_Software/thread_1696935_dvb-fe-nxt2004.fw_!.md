---
title: "dvb-fe-nxt2004.fw !?"
date: 2011-02-28
forum: Multimedia Software
---

### Post by IRONMAN-NC on 2011-02-28
Why is this file so ridiculously hard to get!? I've tried get_dvb_firmware modified, unmodified, 20 fricken different google hits wasted hours and I still can't get the file.   ](*,)

Help, please? :)

[SIZE=4][COLOR=Red]**Solution from this thread:**[/COLOR][/SIZE]

[http://ubuntuforums.org/showthread.php?t=1343172&highlight=dvb-fe-nxt2004.fw](http://ubuntuforums.org/showthread.php?t=1343172&highlight=dvb-fe-nxt2004.fw)

```

sudo aptitude install linux-source
cd /usr/src
sudo tar xvjf linux-source-[INSERT YOUR KERNEL HERE- just do an ls].tar.bz2
cd linux-source-[INSERT YOUR KERNEL VERSION]/Documentation/dvb
sudo perl get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware/

```

---

### Post by An Sanct on 2011-02-28
Well, according to this part of a script, taken from [URL="http://alinux.tv/Kernel-2.6.34/dvb/get_dvb_firmware"]here
[/URL]
```

sub nxt2004 {
  my $sourcefile = "AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip";     
  my $url = "http://www.avermedia-usa.com/support/Drivers/$sourcefile";     
  my $hash = "111cb885b1e009188346d72acfed024c";     
  my $outfile = "dvb-fe-nxt2004.fw";     
  my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);      

  checkstandard();      
  wgetfile($sourcefile, $url);     
  unzip($sourcefile, $tmpdir);     
  verify("$tmpdir/3xHybrid.sys", $hash);     
  extract("$tmpdir/3xHybrid.sys", 465304, 9584, $outfile);      
  $outfile; 
}
```

It seems to just extract the file from 3xHybrid.sys to dvb-fe-nxt2004.fw

Or am I missing something?

---

### Post by IRONMAN-NC on 2011-02-28
And this is what I get time and again


captivate@Jarvis:~/Downloads$ perl get_dvb_firmware nxt2004
unzip failed - unable to extract firmware at get_dvb_firmware line 381.

---

### Post by johntaylor1887 on 2011-02-28
> **IRONMAN-NC said:**
> And this is what I get time and again


captivate@Jarvis:~/Downloads$ perl get_dvb_firmware nxt2004
unzip failed - unable to extract firmware at get_dvb_firmware line 381.
Install P7zip-full and try it. Just right click to unzip.

---

### Post by IRONMAN-NC on 2011-02-28
> **johntaylor1887 said:**
> Install P7zip-full and try it. Just right click to unzip.

From what I understand, []("http://ubuntuforums.org/showthread.php?t=1696935")the file is embedded in another file and can only be extracted with the get_dvb_firmware script. Thanks though.

---

### Post by An Sanct on 2011-03-01
Yes, I understood this line so too:

extract("$tmpdir/3xHybrid.sys", 465304, 9584, $outfile); 

extract(FromFile, Offset, Length, OutFile);

---

### Post by IRONMAN-NC on 2011-03-02
Still no joy

---

### Post by LarryJ2 on 2011-06-17
Following directions contained in the link from Ironman-NC above,  I extracted the referenced firmware file and placed it in the attached zip. 

Apparently  Mythbuntu NATTY [Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic x86_64)] also has the problem of the missing firmware which rendered my ATSC KWorld 110 tuner card inop. When I was "scanning for channels" in MythTV-Backend setup, no channels showed up.  Looking for a solution I spied this in dmesg:

> [   13.170147] DVB: registering adapter 1 frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   13.190140] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   13.191701] nxt2004: Waiting for firmware upload(2)...
[   13.191703] nxt2004: No firmware uploaded (timeout or file not found?)
[

Which clearly suggested the firmware was missing.  Sure enough dvb-fe-nxt2004.fw wasn't in /lib/firmware

Just extract the dvb-fe-nxt2004.fw from the Zip archive then copy to your Mythtv /lib/firmware directory.  The extracted file is 9584 in length.

---

