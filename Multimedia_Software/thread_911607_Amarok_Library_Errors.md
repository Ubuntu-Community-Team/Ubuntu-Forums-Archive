---
title: "Amarok Library Errors"
date: 2008-09-05
forum: Multimedia Software
---

### Post by momalle1 on 2008-09-05
I did a search and couldn't find anything...

Basically, when I scan my library, Amarok comes up with a list of errors of files it can't process, though it doesn't say why. The directory is /home/mike/Music but Music is really a mapped drive, mapped via fstab to the default Music folder. The share is on a Win23k server.

The errors are

[I]The Collection Scanner was unable to process these files:
/home/mike/Music/Aldo Nova/[1997] Nova's Dream/Aldo Nova - 09 - Freedom.mp3
/home/mike/Music/Asia/Astra/AlbumArt_{6EF6C205-F6D5-4A22-A3B2-181EA9CD3BEA}_Large.jpgnne`
/home/mike/Music/Elvis/[2001] The Concert Years/Elvis Presley - 23 - Can't Help Falling In Love Clo.mp3list="" /x
/home/mike/Music/Garth Brooks/[1998] Double Live/Disc 1/Garth Brooks - 10 - It's Your Song (Live).mp3MAGIC" />
/home/mike/Music/Joan Jett/[1991] Notorious/Joan Jett And The Blackhearts - 04 - Lie To Me.mp3 /h
/home/mike/Music/Judas Priest/Point Of Entry/Judas Priest - 10 - On The Run.mp3"X
/home/mike/Music/Randy Travis/Folder.jpg0
/home/mike/Music/Rock - Classic/Steve Miller Band - Jet Airliner.mp3!
/home/mike/Music/Some Girls/[2006] Crushing Love/folder.jpgei[/I]

The first file looks normal, so I don't know why there is an issue, the others have grammatical errors (for lack of a better term) in this list, but NOT when I look at them in Nautilus or Explorer from a Windows box. "*Some Girls/[2006] Crushing Love/folder.jpgei*" says "*Some Girls/[2006] Crushing Love/folder.jpg*" I looked at these files in tag editors and hex editors and don't see the problem there either. Where is Amarok getting this information? Odd also, I have a Blue Oyster Cult folder with the dots over the u, Amarok doesn't give me an error, but doesn't catalog the folder either and Nautilus gives it some random characters and adds (bad encoding) at the end of the folder name. Do I need to add soemthing for special characters in Nautilus?

---

### Post by teethlikelions on 2008-09-13
two things:

first, i am having this exact same issue. almost.
my issue is the same but WITHOUT and network shares. everyone on the internet has the same problem as you when reading your amarok collection from a network share. from what i've gleaned from these countless reposts it has something to do with your read/write permission on the share. there is an amarok+samba page in the amarok wiki that addresses this (i hear).

my issue, though, is in the middle of a mounted usb hard drive. I have full read/write access to it and the other 4500 mp3s on it scanned into my amarok collection just fine.

At first I thought it may have been stemming from the characters in the names. One folder had a '&,' one had a '!,' and one had a few commas. I removed all of these from the folder names, file names, and iD3 tags and amarok still chokes on them.

What gives?
I just spent all day battling my iPod Touch down to firmware 1.1.4 so I could sync with amarok... I am NOT giving up on it now!

Any ideas?

---

