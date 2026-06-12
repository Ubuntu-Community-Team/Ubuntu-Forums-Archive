---
title: "KWorld 115 Firmware install problem"
date: 2009-08-15
forum: Mythbuntu
---

### Post by a3uge on 2009-08-15
I have a KWorld ATSC-115 card. I am setting up Mythbuntu as the only use on my pc. I live in the USA and have Comcast Cable, which is split about 20 times going into different rooms. So I'm assuming it's QAM-64? But I could be wrong on that.

I'm following the instructions at these two places:
[http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld](http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld)
[http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_115](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_115)

And I haven't gotten very far. I hit a road block at:

```

alex@alex-media:/usr/share/doc/linux-doc-2.6.28/dvb$ sudo perl get_dvb_firmware nxt2004
unzip failed - unable to extract firmware at get_dvb_firmware line 421.

```

I can't figure out why it won't unzip. It's very frusterating, there seems to be no place on the internet that lists the same problem. Any tips/ideas would be greatly appreciated.

edit: This is the code around where it fails.
```

sub unzip {
    my ($sourcefile, $todir) = @_;

    $status = system("unzip -q -o -d \"$todir\" \"$sourcefile\" 2>/dev/null" );
    if ((($status >> 8) > 2) || (($status & 0xff) != 0)) {
	die ("unzip failed - unable to extract firmware");
    }
}

```

---

### Post by a3uge on 2009-08-15
For records sake in case this turns up on google or something. The reason why I was getting that error was because the script can only run once. So every time I reran the script, I had to sudo rm -r the dvb directory and install the packages from synaptic again.

Anyways, the problem was a 404 error that prevented me from getting the firmware. The Wiki even said that a 404 error happens in Mythbuntu, but all you needed to do was edit the script and take the www. from the url. So about 3 hours of tinkering I finally found out that they moved their domain from aver.com to [www.avermedia-usa.com](www.avermedia-usa.com). Plugging that in resolved the issue.

So I'm going to the wiki and editing the issue in, I'm not sure who runs or updates the master thing, but that's something that needs to be fixed bad.

---

### Post by B34N on 2009-10-20
I have been havnig trouble following the instructions on the Wiki.  Do you think the reason why I am getting the message "This firmware requires the unzip command - see ftp://ftp.info-zip.org/pub/infozip/UnZip.html" when I try "sudo perl get_dvb_firmware nxt2004" is because the script ran once during Mythbuntu setup?  The "get_dvd_firmware.gz" was in "/usr/share/doc/linux-doc-2.6.28/dvb" and that's where I extracted it to.  Are you saying that I need to remove the dvb directory?

Thank you

---

### Post by klc5555 on 2009-10-20
> **st8ofmi9d said:**
> I have been havnig trouble following the instructions on the Wiki.  Do you think the reason why I am getting the message "This firmware requires the unzip command - see ftp://ftp.info-zip.org/pub/infozip/UnZip.html" when I try "sudo perl get_dvb_firmware nxt2004" is because the script ran once during Mythbuntu setup?  The "get_dvd_firmware.gz" was in "/usr/share/doc/linux-doc-2.6.28/dvb" and that's where I extracted it to.  Are you saying that I need to remove the dvb directory?

Thank you

I'd take the error at face value: do you have the "unzip" package installed?

---

### Post by B34N on 2009-10-20
> **klc5555 said:**
> I'd take the error at face value: do you have the "unzip" package installed?

Thank you!  I feel really silly.  I ASSumed gzip was all it needed.

Moving along now.

---

