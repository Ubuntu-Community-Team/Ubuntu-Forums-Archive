---
title: "Mythtv International characters in Filenames unrecognised"
date: 2010-08-18
forum: Mythbuntu
---

### Post by b1acksun on 2010-08-18
Problem - a number of files use Mandarin characters as their filenames and within their filenames; since upgrading to 0.23 and moving to Mythbuntu they have been unavailable via mythtv but useable by directly selecting them through Dolphin Filemanager and others.

Checked localisation configs, made sure files were installed for the correct regions - even added extra fonts.
Result:did not resolve issue.

Because many of my files are now resident on a newly built FREENAS server, plus I'd also just moved from MYTHDORA to MYTHBUNTU (Compatability issue with my new Asrock boards - FC10/12/13 Just wont install, can't find storage device error; very bad),

Carried out searches for foreign filename issue and got seriously misled as to the possible fault locations, I'd assumed from search results that it was a case of files not been read correctly by Samba/CIFS as all my non-latin characterset files were on the FREENAS Server.

Took a good 3 weeks of the above and altering my samba/fstab settings on various machines also on the FREENAS Box; finally coming to the conclusion of NO Error.
Result:No Resolution  Much of the web search answers were to rename all the 
non-compliant filenames.
This would not of really solved the problem and what is a  non-compliant filename! All Filenames within the specifications should work.

After the samba changes, my share mount in /etc/fstab now contains this.

//xxx.xxx.xxx.xxx/BF_R00_POOL/Video    /home/name/storage/videos/Video    cifs    iocharset=utf8,username="",password="",file_mode=0777,dir_mode=0777 0 0 //xxx.xxx.xxx.xxx/BF_R00_POOL/VideoK    /home/name/storage/videos/VideoK    cifs    iocharset=utf8,username="",password="",file_mode=0777,dir_mode=0777 0 0 //xxx.xxx.xxx.xxx/BF_R00_POOL/Audio    /home/name/storage/music/Audio    cifs    iocharset=utf8,username="",password="",file_mode=0777,dir_mode=0777 0 0 //xxx.xxx.xxx.xxx/BF_R00_POOL/Pictures_and_Films_NFW    /home/name/storage/pictures    cifs    iocharset=utf8,username="",password="",file_mode=0777,dir_mode=0777 0 0

Basically how it was before, apart from the 'iocharset=utf8' entries as this wasn't needed under MYTHDORA.
Tested MYTHTV 'scan for changes' Result:No Additional files.

Whilst browsing my directories across the LAN and locally by using various filemanagers and browsers (Dolphin, Nautilus, Konqueror, FireFox, Opera) came to realise the filenames were fully intact and displaying correctly and had been all the time.
So decided to check if the sessions themselves were been launched as UTF8 environments.
Result:dead end - they were, well at least the ones that I'd been using.
/usr/share/xsessions/kde.desktop
[Desktop Entry]
Encoding=UTF-8
Name=KDE
Comment=Use this session to run MythTV
Exec=/usr/local/bin/mythtv.sh
Icon=
Type=Application

The next try was the following:
Reason: Thought that perhaps the problem was, the filenames had been read as UTF-8, but the mysql database was the point of failure in that for some reason, the
configuration at best was wrong and accepting only latin.
At worst had been coded in a none too flexible manner limiting the type of characters it would handle.
First check was the configuration idea.

Step 1 started with BACKING UP THE MYTHTV DATABASE and the my.cnf file.
sudo cp /etc/mysql/my.cnf /etc/mysql/my.cnf.bak
/usr/share/mythtv/mythconverg_backup.pl --verbose

Added the following to the MYSQL config file (/etc/mysql/my.cnf)
[mysqld]
init_connect='SET collation_connection = utf8_general_ci'
init_connect='SET NAMES utf8'
default-character-set=utf8 character-set-server=utf8
collation-server=utf8_general_ci
skip-character-set-client-handshake

Tested MYTHTV 'scan for changes'  First making the FREENAS Server inaccessible - makes MYTHTV remove entries which it can't find - empty Database.
Making the FREENAS Server accessible and then 'scan for changes' - refills the Database entries
Result: No change, still cannot see non-latin named files.

Spent time checking the MYSQL program, making sure all was installed -  no missing parts.

Decided to look at another problem the mythbuntu box had; that of not playing ISO files.  while reading various searched articles, noticed that some people were basically saying, because they were using Storage Groups is the reason that alternative players wouldnt work at all, and their answers seem to hint at the real reason been that the location details of the files were been passed incorrectly to these players.

This was great news - as it seemed to suggest that the filehandling was going through the Storage Groups Manager which said to me - what if SG not only affected alternate players negatively.

Went to the MYTHTV BACKEND CONFIGURE, scrolled to Storage Groups and removed the Storage Group 'Videos' where my links and actual local files for Video were related to.

Tested MYTHTV 'scan for changes' First making the FREENAS Server inaccessible - forcing the Database entries to empty. Making the FREENAS Server accessible and then 'scan for changes' - refilling the Database entries.
Result: Excellent - all my files from the FREENAS Server and Local Drives with latin and no-latin names appeared and were fully accessible, best of all the ISO files were now ok - stoneage DVD jobless again (sorry).

Just to check this positive result was just not dumb luck - restored the Storage Groups 'Videos'
Result: Bang system not picking up non-latin filenames.

Removed the Storage Groups 'Videos', checked for full function - everything ok.  Restored the original MYSQL /etc/mysql/my.cnf file. Tested MYTHTV 'scan for changes' First making the FREENAS Server inaccessible - forces the Database entries to empty. Making the FREENAS Server accessible and then 'scan for changes' - refills the Database entries.
Result: Everything working, still can see non-latin named files and playback ISO.

This is leading me to believe Storage Groups is at fault here too - hopefully future updates will resolve the problem.

Setup:Mythbuntu 10.04 Combined Frontend and Backend System

name@x:~$ mythfrontend --version
Please include all output in bug reports. MythTV Version   : 24158 MythTV Branch    : branches/release-0-23-fixes Network Protocol : 56 Library API      : 0.23.20100314-1 QT Version       : 4.6.2 Options compiled in:  linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

name@x:~$ mythbackend --version
Please include all output in bug reports. MythTV Version   : 24158 MythTV Branch    : branches/release-0-23-fixes Network Protocol : 56 Library API      : 0.23.20100314-1 QT Version       : 4.6.2 Options compiled in:  linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

name@x:~$ mysql --version
mysql  Ver 14.14 Distrib 5.1.41, for debian-linux-gnu (x86_64) using readline 6.1

Dolphin Version 1.4 Using KDE Development Platform 4.4.2 (KDE 4.4.2)

Hardware. M/B:M3A790GMH/128, CPU:AMD Phenom(tm) II X4 20 Processor, RAM:4GB DDR3 1333, Video Card:Nvidia Geforce 210, HDD:1TB Samsung, 120GB Deskstar, 2xNova T-500

Hope this helps.

---

### Post by Milan Knizek on 2010-10-16
I came accross a similar problem (Mythbuntu 10.10) and while I have not found the solution, there was at least a workaround for me.

What does not work:
SMB share //server/media/videos is mounted at /mythtv/videos;
MythVideo looks at /mythtv/videos for movies;
Then the filenames with accented characters are not shown in MythVideo at all.

What does work:
SMB share //server/media (!) is mounted at /mythtv/media;
MythVideo looks at /mythtv/media/videos for movies;
Then everything's fine - all files are shown in MythVideo.

MythVideo behaves the same way also with NFS exports. The filenames show correctly in file managers in both cases. I did not have the network shares setup for MythVideo in Mythbuntu 10.04 so I cannot say if it had worked or not.

---

### Post by andree_b on 2010-10-19
There was a problem with 9.04 or 9.10 where it started the backend before the correct locale was set which lead to not recognizing foreign characters... did you try to restart mythbackend from properly configured shell?

---

### Post by b1acksun on 2010-10-24
Having allowed Samba to be upgraded on all my networked machines, after rebooting the machines to allow a clean Samba start, to my horror couldn't see any machines or directories on my network.

The Mythbuntu box was partially affected it was able to get get files from the Freenas NAS Box, trying to browse failed with the Server Timeout Message.

Using smb://xxx.xxx.xxx.xxx in the url of Dolphin or firefox did allow browsing; telling me that Samba was generally fine and that it was likely to be a configuration issue.

Plenty of experiments with the /etc/samba/smb.conf - gave me the following apparent fix.

name resolve order = lmhosts bcast host


The default for samba is:
name resolve order = lmhosts wins hosts bcastHope this is useful.

---

