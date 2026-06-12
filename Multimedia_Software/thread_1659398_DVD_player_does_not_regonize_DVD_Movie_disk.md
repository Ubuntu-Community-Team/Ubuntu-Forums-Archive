---
title: "DVD player does not regonize DVD Movie disk"
date: 2011-01-04
forum: Multimedia Software
---

### Post by wdhpr on 2011-01-04
Hello
I'm running Ubuntu 10.10
My cd/dvd player recognizes game and data CD'S/DVD'S the cd/dvd icon appears on desktop and I can access the file as well as playing games off the cd's.

When I try movie DVD's I get no desktop icon nor is it shown in the file managers. When trying to access the movie via VLC (open disk) I get the following error:
Playback failure:
DVDRead could not open the disc "/dev/dvd".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details. (Don't know what log its referring to)
SMplayer and xine won't work either

I have tried every tip I could find on this forum. I installed all restricted format files including** libdvdread4 **and then ran this command
 sudo /usr/share/doc/libdvdread4/install-css.sh

followed all the advice from this [restricted formats/playing dvd's]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

Its like the drive won't recognize a movie DVD. 

Just as a side not I use to run simply mepis with no issues with 
movie dvd's. I also dual boot to Winxp no problems their either

Help](*,)

Thanks in advance
Wdhpr

---

### Post by BicyclerBoy on 2011-01-04
The vlc log file should be displayed at the error.

Try vlc menu tools/messages    leave this open.
Try to access the DVD.
read the error message.

Open synaptic package manager & double check the libdvdread libdvdnav & libdvdcss packages are installed.

There are additional notes for problem solving on the link you posted.
Is your user a member of the cdrom group ? Permissions ?

You will need a recent VLC or mplayer or MythTV (0.24) to access latest DVDs.
Some take 1 minute to open...

I would recommend finding a 3rd party ppa of your favourite player.

---

### Post by wdhpr on 2011-01-04
> **BicyclerBoy said:**
> The vlc log file should be displayed at the error.

Try vlc menu tools/messages    leave this open.
Try to access the DVD.
read the error message.

Open synaptic package manager & double check the libdvdread libdvdnav & libdvdcss packages are installed.

There are additional notes for problem solving on the link you posted.
Is your user a member of the cdrom group ? Permissions ?

You will need a recent VLC or mplayer or MythTV (0.24) to access latest DVDs.
Some take 1 minute to open...

I would recommend finding a 3rd party ppa of your favourite player.

Thanks for the response.
Yes those files are installed.
Here are vlc's error message with messages left open:
dvdread error: DVDRead cannot open source: /dev/dvd
main error: open of `dvd:///dev/dvd' failed: (null)


[COLOR=Red]dvd:///dev/dvd[/COLOR] This looks odd. shouldn't it be /dev/sr0 or something.

Like I said I cant even access a video dvd.

bash: vlc/dev/sro: No such file or directory
root@wdhpr-W3644:/home/wdhpr# vlc/dev/sr0
bash: vlc/dev/sr0: No such file or directory
root@wdhpr-W3644:/home/wdhpr# vlc/sro
bash: vlc/sro: No such file or directory
root@wdhpr-W3644:/home/wdhpr# vlc/sr0
bash: vlc/sr0: No such file or directory
root@wdhpr-W3644:/home/wdhpr# vlc/dev/dvd
bash: vlc/dev/dvd: No such file or directory
root@wdhpr-W3644:/home/wdhpr# vlc/dev/cd
bash: vlc/dev/cd: No such file or directory
root@wdhpr-W3644:/home/wdhpr# 

Music cd's, data cd/dvd's no problem.

Hera are some snap shots.
1) Disk utility showing the dvd drive with a Meois live cd on a dvd disk
2) disk utility showing the dvd drive with a Movie D=dvd disk
3) this shows the command  **vlc /dev/sr0**

---

