---
title: "ntfs + huge music collection = Dead Pulse Audio?"
date: 2009-07-26
forum: Multimedia Software
---

### Post by ShepHeard on 2009-07-26
I'm not sure what's happening, but...

Check most of my posts and you will see I have had nothing but problems with my sound (no mic, etc etc ad infinitum ad nauseum). Having spent hours a night for many nights/weeks/months I'm convinced that it's Pulse Audio. I've now gone off to pastures new (blue?) with Kubuntu, and everything works. So far.

Anyway, my flat mate uses Ubuntu 9.04 on a 64 bit Toshiba, and everything has always worked 'out-of-the-box". Until now. He plugged in my external USB drive (160 gb, ntfs formatted) to check out my music collection. He clicked on the music folder (80 gb of music in a variety of formats) and suddenly his sound crashed. Lots of re-boots, etc, nothing. Finally he removed pulse audio and set everything to ALSA and his sound is working again. 

Is there any reason for this? Is it just a coincidence, or does Pulse have issues with ntfs drives? And why?

For a couple of nights he had a glimpse into my world of rage and frustration with getting sound to work in Ubuntu 9.04, and he didn't like it. He now wants nothing more to do with Pulse Audio, and I can't blame him...

Anyway - I don't think that this is a call for help, but just a curiosity... Anyone else experienced the same things? Or has any ideas?

Cheers,

:)

---

### Post by ajgreeny on 2009-07-26
I really don't think that ntfs has anything to do with it at all, and can see no reason for 80GB+ of files to be a problem either.  Certainly I can play mp3s from my windows ntfs partition without any difficulty at all using the default sound setup of jaunty, ie pulse.

I hope you get it sorted soon.

---

### Post by ShepHeard on 2009-07-26
Yeah, that's what I thought. But it's just too much of a coincidence... My little external ntfs drive is the common deninator.. Have I found a Linux virus..! :p

Well, it's sorted after a fasion - we are both now Pulse Audio free.

---

### Post by ajgreeny on 2009-07-26
Great, but shouldn't have been necessary to remove pulse to get it working.  Very weird!

---

### Post by igorzwx on 2009-07-26
PulseAudio is not a virus,
it is rather a trojan, or rootkit, if you want.

---

### Post by ShepHeard on 2009-07-27
@ajgreeny: Strange indeed, I agree. It shouldn't be necessary to remove Pulse, but it seems to be the only way... I am still curious as to know why clicking on the music folder crashed Pulse though... I'd report it as a bug, but I'm not sure with what..!

@igor: Ha ha - I was actually implying that there was a 'virus' on my external drive, but well... you could be right... ;o)

---

### Post by igorzwx on 2009-07-27
It seems that this joke is not a 100% joke.
Today, I received a message from a friend.
You cannot read in Russian, but, nevertheless...
Try to translate it with Google
(vulnerability in Linux kernel + PulseAudio)

[http://www.linux.org.ru/view-message.jsp?msgid=3880660&lastmod=1248006083738&pa](http://www.linux.org.ru/view-message.jsp?msgid=3880660&lastmod=1248006083738&pa)
**     &#1048;&#1085;&#1090;&#1077;&#1088;&#1077;&#1089;&#1085;&#1072;&#1103; &#1091;&#1103;&#1079;&#1074;&#1080;&#1084;&#1086;&#1089;&#1090;&#1100; &#1074; &#1103;&#1076;&#1088;&#1077; Linux     **

 &#1040;&#1074;&#1090;&#1086;&#1088; &#1087;&#1088;&#1086;&#1077;&#1082;&#1090;&#1072; [grsecurity]("http://grsecurity.net/"), Brad Spengler, &#1086;&#1087;&#1091;&#1073;&#1083;&#1080;&#1082;&#1086;&#1074;&#1072;&#1083; [&#1101;&#1082;&#1089;&#1087;&#1083;&#1086;&#1081;&#1090;]("http://grsecurity.net/%7Espender/cheddar_bay.tgz"), &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1102;&#1097;&#1080;&#1081; &#1086;&#1095;&#1077;&#1085;&#1100; &#1080;&#1085;&#1090;&#1077;&#1088;&#1077;&#1089;&#1085;&#1091;&#1102; &#1091;&#1103;&#1079;&#1074;&#1080;&#1084;&#1086;&#1089;&#1090;&#1100; &#1074; &#1103;&#1076;&#1088;&#1077; Linux (&#1076;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088; net/tun).&#1057;&#1087;&#1077;&#1094;&#1080;&#1092;&#1080;&#1082;&#1072; &#1101;&#1090;&#1086;&#1081; &#1091;&#1103;&#1079;&#1074;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080; &#1089;&#1086;&#1089;&#1090;&#1086;&#1080;&#1090; &#1074; &#1090;&#1086;&#1084;, &#1095;&#1090;&#1086; &#1091;&#1103;&#1079;&#1074;&#1080;&#1084;&#1086;&#1089;&#1090;&#1100; &#1086;&#1090;&#1089;&#1091;&#1090;&#1089;&#1090;&#1074;&#1091;&#1077;&#1090; &#1074; &#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1086;&#1084; &#1082;&#1086;&#1076;&#1077;, &#1085;&#1086; &#1087;&#1088;&#1080;&#1089;&#1091;&#1090;&#1089;&#1090;&#1074;&#1091;&#1077;&#1090; &#1074; &#1073;&#1080;&#1085;&#1072;&#1088;&#1085;&#1086;&#1084;. &#1050;&#1072;&#1082; &#1090;&#1072;&#1082;&#1086;&#1077; &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;? &#1044;&#1072;&#1074;&#1072;&#1081;&#1090;&#1077; &#1088;&#1072;&#1089;&#1089;&#1084;&#1086;&#1090;&#1088;&#1080;&#1084; &#1101;&#1090;&#1086; &#1085;&#1072; &#1087;&#1088;&#1080;&#1084;&#1077;&#1088;&#1077;. &#1042;&#1089;&#1077; &#1085;&#1072;&#1095;&#1080;&#1085;&#1072;&#1077;&#1090;&#1089;&#1103; &#1089; &#1090;&#1086;&#1075;&#1086;, &#1095;&#1090;&#1086; &#1087;&#1088;&#1086;&#1080;&#1089;&#1093;&#1086;&#1076;&#1080;&#1090; &#1080;&#1085;&#1080;&#1094;&#1080;&#1072;&#1083;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103; &#1091;&#1082;&#1072;&#1079;&#1072;&#1090;&#1077;&#1083;&#1103; sk: 
struct sock *sk = tun->sk;
 &#1069;&#1090;&#1086;&#1090; &#1082;&#1086;&#1076; &#1085;&#1077; &#1074;&#1099;&#1079;&#1099;&#1074;&#1072;&#1077;&#1090; &#1086;&#1096;&#1080;&#1073;&#1086;&#1082; &#1076;&#1072;&#1078;&#1077; &#1077;&#1089;&#1083;&#1080; tun == NULL, &#1080; &#1085;&#1077; &#1103;&#1074;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1089;&#1072;&#1084; &#1087;&#1086; &#1089;&#1077;&#1073;&#1077; &#1091;&#1103;&#1079;&#1074;&#1080;&#1084;&#1086;&#1089;&#1090;&#1100;&#1102;.&#1053;&#1077;&#1089;&#1082;&#1086;&#1083;&#1100;&#1082;&#1080;&#1084;&#1080; &#1089;&#1090;&#1088;&#1086;&#1082;&#1072;&#1084;&#1080; &#1085;&#1080;&#1078;&#1077; &#1087;&#1088;&#1086;&#1080;&#1089;&#1093;&#1086;&#1076;&#1080;&#1090; &#1087;&#1088;&#1086;&#1074;&#1077;&#1088;&#1082;&#1072; &#1080;&#1085;&#1080;&#1094;&#1080;&#1072;&#1083;&#1080;&#1079;&#1072;&#1094;&#1080;&#1080; &#1091;&#1082;&#1072;&#1079;&#1072;&#1090;&#1077;&#1083;&#1103; tun: 
if (!tun)
        return POLLERR;
 &#1050;&#1072;&#1079;&#1072;&#1083;&#1086;&#1089;&#1100; &#1073;&#1099;, &#1090;&#1077;&#1087;&#1077;&#1088;&#1100; &#1074;&#1089;&#1077; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1100;&#1085;&#1086;. &#1047;&#1083;&#1086;&#1076;&#1077;&#1081; &#1085;&#1077; &#1087;&#1088;&#1086;&#1081;&#1076;&#1077;&#1090;.&#1053;&#1086;! &#1055;&#1088;&#1080; &#1089;&#1073;&#1086;&#1088;&#1082;&#1077; &#1082;&#1086;&#1076;&#1072; &#1082;&#1086;&#1084;&#1087;&#1080;&#1083;&#1103;&#1090;&#1086;&#1088; &#1087;&#1086;&#1083;&#1072;&#1075;&#1072;&#1077;&#1090;, &#1095;&#1090;&#1086; &#1091;&#1082;&#1072;&#1079;&#1072;&#1090;&#1077;&#1083;&#1100; tun &#1091;&#1078;&#1077; &#1082;&#1086;&#1088;&#1088;&#1077;&#1082;&#1090;&#1085;&#1086; &#1080;&#1085;&#1080;&#1094;&#1080;&#1072;&#1083;&#1080;&#1079;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085; &#1080;, &#1086;&#1087;&#1090;&#1080;&#1084;&#1080;&#1079;&#1080;&#1088;&#1091;&#1103; &#1082;&#1086;&#1076;, &#1074;&#1099;&#1082;&#1080;&#1076;&#1099;&#1074;&#1072;&#1077;&#1090; &#1087;&#1088;&#1086;&#1074;&#1077;&#1088;&#1082;&#1091; &#1092;&#1072;&#1082;&#1090;&#1072; &#1080;&#1085;&#1080;&#1094;&#1080;&#1072;&#1083;&#1080;&#1079;&#1072;&#1094;&#1080;&#1080; (&#1087;&#1088;&#1080;&#1074;&#1077;&#1076;&#1077;&#1085;&#1085;&#1099;&#1081; &#1074;&#1099;&#1096;&#1077; &#1086;&#1087;&#1077;&#1088;&#1072;&#1090;&#1086;&#1088; if). &#1058;&#1072;&#1082;&#1080;&#1084; &#1086;&#1073;&#1088;&#1072;&#1079;&#1086;&#1084;, &#1085;&#1080;&#1095;&#1090;&#1086; &#1085;&#1077; &#1084;&#1077;&#1096;&#1072;&#1077;&#1090; &#1079;&#1083;&#1086;&#1091;&#1084;&#1099;&#1096;&#1083;&#1077;&#1085;&#1085;&#1080;&#1082;&#1091; &#1079;&#1072;&#1089;&#1090;&#1072;&#1074;&#1080;&#1090;&#1100; &#1103;&#1076;&#1088;&#1086; &#1086;&#1073;&#1088;&#1072;&#1097;&#1072;&#1090;&#1100;&#1089;&#1103; &#1087;&#1086; &#1085;&#1091;&#1083;&#1077;&#1074;&#1086;&#1084;&#1091; &#1072;&#1076;&#1088;&#1077;&#1089;&#1091;. &#1048;&#1084;&#1077;&#1077;&#1084; &#1082;&#1083;&#1072;&#1089;&#1089;&#1080;&#1095;&#1077;&#1089;&#1082;&#1091;&#1102; null pointer dereference vulnerability.
&#1054;&#1073;&#1085;&#1072;&#1088;&#1091;&#1078;&#1077;&#1085;&#1085;&#1072;&#1103; &#1091;&#1103;&#1079;&#1074;&#1080;&#1084;&#1086;&#1089;&#1090;&#1100; &#1087;&#1086;&#1079;&#1074;&#1086;&#1083;&#1103;&#1077;&#1090; &#1079;&#1083;&#1086;&#1091;&#1084;&#1099;&#1096;&#1083;&#1077;&#1085;&#1085;&#1080;&#1082;&#1091; &#1086;&#1073;&#1086;&#1081;&#1090;&#1080; &#1086;&#1075;&#1088;&#1072;&#1085;&#1080;&#1095;&#1077;&#1085;&#1080;&#1103; SELinux/AppArmor, &#1074;&#1099;&#1079;&#1074;&#1072;&#1090;&#1100; &#1082;&#1088;&#1072;&#1093; &#1103;&#1076;&#1088;&#1072; &#1083;&#1080;&#1073;&#1086; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1083;&#1100;&#1085;&#1099;&#1081; &#1082;&#1086;&#1076; &#1089; &#1088;&#1091;&#1090;&#1086;&#1074;&#1099;&#1084;&#1080; &#1087;&#1088;&#1080;&#1074;&#1080;&#1083;&#1077;&#1075;&#1080;&#1103;&#1084;&#1080;.
&#1055;&#1088;&#1077;&#1076;&#1089;&#1090;&#1072;&#1074;&#1083;&#1077;&#1085;&#1085;&#1099;&#1081; &#1089;&#1087;&#1083;&#1086;&#1081;&#1090; &#1087;&#1088;&#1086;&#1090;&#1077;&#1089;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085; &#1085;&#1072; &#1103;&#1076;&#1088;&#1072;&#1093; &#1074;&#1077;&#1088;&#1089;&#1080;&#1081; 2.6.30 &#1089; SELinux &#1080; &#1073;&#1077;&#1079;, &#1072; &#1090;&#1072;&#1082;&#1078;&#1077; &#1085;&#1072; 2.6.18 (RHEL5, &#1089;&#1086;&#1073;&#1080;&#1088;&#1072;&#1090;&#1100; &#1089; &#1086;&#1087;&#1094;&#1080;&#1077;&#1081; -DRHEL5_SUCKS). &#1044;&#1083;&#1103; &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086;&#1081; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099; &#1076;&#1072;&#1085;&#1085;&#1086;&#1075;&#1086; &#1089;&#1087;&#1083;&#1086;&#1081;&#1090;&#1072; &#1085;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1085;&#1072;&#1083;&#1080;&#1095;&#1080;&#1077; &#1085;&#1072; &#1084;&#1072;&#1096;&#1080;&#1085;&#1077; PulseAudio &#1080; &#1087;&#1086;&#1076;&#1075;&#1088;&#1091;&#1078;&#1077;&#1085;&#1085;&#1086;&#1075;&#1086; &#1084;&#1086;&#1076;&#1091;&#1083;&#1103; tun.
&#1041;&#1086;&#1083;&#1077;&#1077; &#1087;&#1086;&#1076;&#1088;&#1086;&#1073;&#1085;&#1091;&#1102; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1102; &#1074;&#1099; &#1084;&#1086;&#1078;&#1077;&#1090;&#1077; &#1087;&#1088;&#1086;&#1095;&#1080;&#1090;&#1072;&#1090;&#1100; &#1074; &#1082;&#1086;&#1084;&#1084;&#1077;&#1085;&#1090;&#1072;&#1088;&#1080;&#1103;&#1093; &#1082; &#1082;&#1086;&#1076;&#1091; &#1101;&#1082;&#1089;&#1087;&#1083;&#1086;&#1081;&#1090;&#1072;.
&#1050;&#1089;&#1090;&#1072;&#1090;&#1080;, &#1101;&#1090;&#1091; &#1091;&#1103;&#1079;&#1074;&#1080;&#1084;&#1086;&#1089;&#1090;&#1100; &#1091;&#1078;&#1077; &#1072;&#1082;&#1090;&#1080;&#1074;&#1085;&#1086; &#1086;&#1073;&#1089;&#1091;&#1078;&#1076;&#1072;&#1077;&#1090; &#1091; &#1085;&#1072;&#1089; &#1074; [&#1090;&#1086;&#1083;&#1082;&#1089;&#1072;&#1093;]("http://www.linux.org.ru/view-message.jsp?msgid=3880416").
>>> [&#1069;&#1082;&#1089;&#1087;&#1083;&#1086;&#1081;&#1090;]("http://grsecurity.net/%7Espender/cheddar_bay.tgz").
&#1052;&#1077;&#1090;&#1082;&#1080;: *[kernel]("http://www.linux.org.ru/view-news.jsp?section=1&tag=kernel"), [security]("http://www.linux.org.ru/view-news.jsp?section=1&tag=security"), [&#1091;&#1103;&#1079;&#1074;&#1080;&#1084;&#1086;&#1089;&#1090;&#1100;]("http://www.linux.org.ru/view-news.jsp?section=1&tag=%D1%83%D1%8F%D0%B7%D0%B2%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D1%8C")*  
 nnz [IMG]http://www.linux.org.ru/img/normal-star.gif[/IMG] ([*]("http://www.linux.org.ru/whois.jsp?nick=nnz")) (17.07.2009 16:43:34)
*&#1055;&#1088;&#1086;&#1074;&#1077;&#1088;&#1077;&#1085;&#1086;: boombick ([*]("http://www.linux.org.ru/whois.jsp?nick=boombick")) 17.07.2009 19:19:06*

---

### Post by igorzwx on 2009-07-27
I googled it and found this:
[http://www.secuobs.com/secumail/btsecumail/msg16602.shtml](http://www.secuobs.com/secumail/btsecumail/msg16602.shtml)
PulseAudio local race condition privilege escalation vulnerability ------------------------------------------------------------------------ Yorick Koster, June 2009  ------------------------------------------------------------------------ Abstract ------------------------------------------------------------------------  The PulseAudio binary is affected by a local race condition. If the  binary is installed as SUID root, it is possible to exploit this  vulnerability to gain root privileges. This attack requires that a local attacker can create hard links on the same hard disk partition on which PulseAudio is installed (i.e. /usr/bin and /tmp reside on the same  partition).

 ------------------------------------------------------------------------ See also ------------------------------------------------------------------------  - CVE-2009-1894 [2] - GLSA 200907-13 [3] PulseAudio: Local privilege escalation - USN-804-1 [4] PulseAudio vulnerability  ------------------------------------------------------------------------ Tested version ------------------------------------------------------------------------  This issue was successfully verified on the following Linux  distributions:  - Ubuntu 9.04 running PulseAudio version 0.9.14 - Debian 5.0 running PulseAudio version 0.9.10 - Mandriva Linux 2009 Spring running PulseAudio version 0.9.15  ------------------------------------------------------------------------ Fix ------------------------------------------------------------------------  A patch for PulseAudio was released that addresses this issue. This  patch can be obtained from the following location:  [link://[click]]("http://git.0pointer.de/?p=pulseaudio.git;a=commit;h=84200b423ebfa7e2dad9b1b65f64eac7bf3d2114")  As a temporary workaround, remove the SUID bit from the PulseAudio  binary.

 $ chmod u-s `which pulseaudio`  ------------------------------------------------------------------------ Introduction ------------------------------------------------------------------------  PulseAudio [5] is a sound server for POSIX and Win32 systems. A sound  server is basically a proxy for your sound applications. It allows you  to do advanced operations on your sound data as it passes between your  application and your hardware.

 On some systems, the PulseAudio binary is installed SUID root to enable  real-time scheduling. If set, the daemon will drop root privileges  immediately on startup, however it will retain the CAP_NICE capability  (on systems that support it), but only if the calling user is a member  of the pulse-rt group. For all other users all capabilities are dropped  immediately.

 ------------------------------------------------------------------------ Race condition ------------------------------------------------------------------------  If the PulseAudio binary is started on Linux systems, it checks if the  LD_BIND_NOW environment variable is set. If this is not the case,  PulseAudio will set the variable and it will reload itself. It tries to  determine its path name by looking at the /proc/self/exe symbolic link.  This symbolic link will point to the full path name of the current  process.

 int main(int argc, char *argv[]) { [...] #if defined(__linux__) && defined(__OPTIMIZE__) 	/* 		Disable lazy relocations to make usage of external libraries 		more deterministic for our RT threads. We abuse __OPTIMIZE__ as 		a check whether we are a debug build or not.

	*/ 	 	if (!getenv("LD_BIND_NOW")) { 		char *rp; 	 		/* We have to execute ourselves, because the libc caches the 		* value of $LD_BIND_NOW on initialization. */ 	 		pa_set_env("LD_BIND_NOW", "1"); 		pa_assert_se(rp = pa_readlink("/proc/self/exe")); 		pa_assert_se(execv(rp, argv) == 0); 	} #endif  Normally, /proc/self/exe will point to something like  /usr/bin/pulseaudio. However by using hard links, it is possible to  cause /proc/self/exe to point to a different location.

 $ cd /tmp $ ls -la /proc/self/exe lrwxrwxrwx 1 yorick yorick 0 2009-06-09 16:31 /proc/self/exe ->  /bin/ls $ ln `which ls` ls $ ./ls -la /proc/self/exe lrwxrwxrwx 1 yorick yorick 0 2009-06-09 16:31 /proc/self/exe ->  /tmp/ls  In addition, if a hard link is created, the SUID bit is preserved.

 $ ln `which pulseaudio` pulseaudio $ ls -la pulseaudio  -rwsr-xr-x 2 root root 71616 2009-04-09 02:12 pulseaudio  A race condition exists in the reload mechanism of PulseAudio. An  attacker can exploit this issue by creating a hard link pointing to the  PulseAudio binary. After this it can execute this binary through the  hard link. At this moment /proc/sef/exe will point to the hard link.  Before PulseAudio is restarted, the attacker can replace the hard link  with a different (executable) file or (symbolic) link. If PulseAudio is  restarted, it will use a path name that at this moment points to a  different file, for example a command shell. Root privileges are not  dropped when PulseAudio is reloading, thus allowing a local attacker to  gain root privileges.

 Please note, this attack is only possible if the attacker can create  hard links on the same hard disk partition on which PulseAudio is  installed (i.e. /usr/bin and /tmp reside on the same partition).

 ------------------------------------------------------------------------ Proof of concept ------------------------------------------------------------------------  The following proof of concept can be used to exploit this issue. The  proof of concept tries to exploit this issue by creating hard links in  the /tmp directory.

 pa_race [6]  $ ./pa_race I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

I: caps.c: Dropping root privileges.

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

N: main.c: Called SUID root and real-time and/or high-priority  scheduling was requested in the configuration. However, we lack the  necessary privileges: N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to  grant us the requested privileges and we have no increase  RLIMIT_NICE/RLIMIT_RTPRIO resource limits.

N: main.c: For enabling real-time/high-priority scheduling please  acquire the appropriate PolicyKit privileges, or become a member of  'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource  limits for this user.

E: pid.c: Daemon already running.

E: main.c: pa_pid_file_create() failed.

[...] uid=0(root) gid=0(root) groups=4(adm), 20(dialout), 24(cdrom),  25(floppy), 29(audio), 30(dip), 44(video), 46(plugdev), 107(fuse),  109(lpadmin), 115(admin), 1000(yorick) #   ------------------------------------------------------------------------ References ------------------------------------------------------------------------  [1] [link://[click]]("http://www.akitasecurity.nl/advisory.php?id=AK20090602") [2] [link://[click]]("http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2009-1894") [3] [link://[click]]("http://www.gentoo.org/security/en/glsa/glsa-200907-13.xml") [4] [link://[click]]("http://www.ubuntu.com/usn/usn-804-1") [5] [link://[click]]("http://pulseaudio.org/") [6] [link://[click]]("http://www.akitasecurity.nl/advisory/AK20090602/pa_race")  ------------------------------------------------------------------------ --  ------------------------------------------------------------------------ Akita Software Security (Kvk 37144957) [link://[click]]("http://www.akitasecurity.nl/") ------------------------------------------------------------------------ Key fingerprint = 5FC0 F50C 8B3A 4A61 7A1F  2BFF 5482 D26E D890 5A65 [link://[click]]("http://keyserver.pgp.com/vkd/DownloadKey.event?keyid=0x5482D26ED8905A65") **Attachment: [signature.asc]("http://www.secuobs.com/secumail/btsecumail/pgpQEzmgT8sdI.pgp")**
*Description:* This is a digitally signed message part
          
[LIST]
[*]Precedent par Date: [[ GLSA 200907-14 ] Rasterbar libtorrent: Directory traversal]("http://www.secuobs.com/secumail/btsecumail/msg16599.shtml")
[*]Suivant par Date: [COMRaider Idefense Labs CreateFolder() and Copy() Insecure Method (Hard Disk Filler Exploit)]("http://www.secuobs.com/secumail/btsecumail/msg16600.shtml")
[*]Precedent par fil : [[ GLSA 200907-14 ] Rasterbar libtorrent: Directory traversal]("http://www.secuobs.com/secumail/btsecumail/msg16599.shtml")
[*]Suivant par fil : [COMRaider Idefense Labs CreateFolder() and Copy() Insecure Method (Hard Disk Filler Exploit)]("http://www.secuobs.com/secumail/btsecumail/msg16600.shtml")
[*]Index(s):
[LIST]
[*][Date]("http://www.secuobs.com/secumail/btsecumail/mail2.shtml#16602")
[*][Fil]("http://www.secuobs.com/secumail/btsecumail/thrd416.shtml#16602")
[/LIST]
 
[/LIST]

---

### Post by igorzwx on 2009-07-27
This is the original message:
**[Root exploit for *Linux kernel* published - News - The H Security [B]...**]("http://www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791")[/B]

17 Jul 2009 **...** *Brad Spengler*, the developer behind the Grsecurity project, has published an exploit for a *vulnerability* in the Tun interface in *Linux kernel* 2.6.30 **...** The exploit uses loadable modules from *PulseAudio* which are set as **...**
[www.h-online.com/security/Root](www.h-online.com/security/Root)...**Linux**-**kernel**.../113791 - [Cached]("http://209.85.135.132/search?q=cache:_Xm8cw6--XkJ:www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791+vulnerability+linux+kernel+PulseAudio+Brad+Spengler&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791")

---

