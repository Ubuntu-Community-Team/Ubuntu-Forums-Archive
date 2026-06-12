---
title: "Recommended Android Apps for Ubuntu Users"
date: 2013-10-18
forum: Mobile Technology Discussions (CLOSED)
---

### Post by SeijiSensei on 2013-10-18
Having just written a post listing a number of Android apps I found useful, I thought I'd check to see if we have an ongoing thread on this topic.  Not finding one, I'm starting it now.

I've had a Galaxy S3 for most of 2013 and have installed a variety of apps that I use in conjunction with my Kubuntu desktops and my Linux servers.  I upgraded to 13.04 just so I could use the MTP protocol to transfer files between my phone and computers.  Current Android versions no longer allow you to mount the phone as a USB Mass Storage Device.  Instead, Android now uses the Media Transfer Protocol (MTP) for which support in Ubuntu was pretty shaky until 13.04 was released.  It still has the occasional glitch, but in general it works well if you want to copy files between a computer and the Android device.  For solutions that do not rely on MTP support, see the section on "network file systems" below.

Here are some apps that I have found useful:

1)  Music
I use the standard player that comes with Android.  It finds most anything stored in a Music folder (and maybe elsewhere though I haven't checked).  I installed a MicroSD card, created a Music folder on that, and copied all of my music there.  The standard player discovers it without any extra effort.  It also supports less common formats like Ogg Vorbis and FLAC.

I also recommend [**Cover Art Downloader**](https://play.google.com/store/apps/details?id=com.birbeck.android.coverart&hl=en) to find missing album covers.  It even found the covers for some Japanese anime CDs and jazz albums from the 50's and 60's.

2) Video
I installed [**MX Player**]("https://play.google.com/store/apps/details?id=com.mxtech.videoplayer.ad&hl=en") which supports a wide variety of formats and subtitles.  It also plays videos encoded in the Hi10P format, which the standard video player does not. I suspect MX Player  is based on the mplayer2 code, but I cannot tell for sure.  There's also a [VLC]("https://play.google.com/store/apps/details?id=org.videolan.vlc.betav7neon&hl=en") app for Android, but it is incompatible with the ARMv6 CPU in my phone.  I don't use VLC on desktops either; I prefer [SMPlayer]("http://smplayer.sourceforge.net/").

I used [VPlayer]("https://play.google.com/store/apps/details?id=me.abitno.vplayer.t&hl=en") for a while but found MX Player superior and switched to that.

3) Terminal sessions
I use [**Android Terminal Emulator**]("https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=en") occasionally for shell sessions using the phone's OS.  Most common Unix commands like ls and ping are available by default.

For remote sessions, I use [**JuiceSSH**]("https://play.google.com/store/apps/details?id=com.sonelli.juicessh&hl=en").  A forthcoming version will add SCP and SFTP to the current terminal client.  Apparently JuiceSSH will also run local terminal sessions as well.  The [**AndFTP**]("https://play.google.com/store/apps/details?id=lysesoft.andftp&hl=en") client supports both SCP and SFTP along with insecure FTP.

Both JuiceSSH and MX Player are compatible with the "Multi-Window" display that lets you switch easily between running applications.

4)  Browsers
I use [**Firefox**]("https://play.google.com/store/apps/details?id=org.mozilla.firefox&hl=en") because I am so familiar with it from years of using it on the desktop.  It supports Firefox sync so you can have the same set of bookmarks on the phone that you have on your desktop.  The default browser is Google Chrome, of course.  Chrome works with Multi-Window, but Firefox does not.

5)  E-Mail
I use the stock client both to communicate with my GMail account and with my local mail server running IMAP.  Mozilla has not released a version of Thunderbird for Android.

6)  Network file systems
One thing you won't be able to do is mount remote file systems using NFS or CIFS (aka SMB).  Unless you root your phone, you cannot create arbitrary mount points in the filesystem.  There are CIFS clients that you can use to access a file share exported with Samba; I use [**AndSMB**]("https://play.google.com/store/apps/details?id=lysesoft.andsmb&hl=en").  

I also have used an app called [**WiFi File Transfer**]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransfer&hl=en") that turns the phone into a webserver.  I used that to transfer files before upgrading to 13.04.  The free version has a limitation on the size of uploaded files, so I spent the $3 to get the "Pro" version. It is much better at bulk file transfers than the FTP and CIFS clients.

If you have some favorite Android apps to share, please join in!  Rather than list every app ever written, I'd prefer that this thread focus just on apps that help make your Android device work better with Linux.

---

