---
title: "My bash script to convert avi to dvd &amp; burn"
date: 2009-12-16
forum: Multimedia Software
---

### Post by aflores3 on 2009-12-16
I've been working with ubuntu for about 3 months. I've made other little simple bash scripts to help me with mundane tasks, but I wanted something to automatically burn a DVD from an avi file. 

I put together the simple little script below. I'm sure to the vast majority of you, it is elementary, but I was quite proud of it. 

My question is, do you have ideas on how to improve it? as it is, it has absolutely NO error checking. I'd like something to check if the media in my dvd burner is blank and either prompt or burn depending on the check.

I'm sure you all can improve my ffmpeg & dvdauthor commands.

The purpose of this is to quickly and easily burn a copy of a movie to play in the dvd player in our vehicle. I want the dvd to be 'autoplay' for that reason.

```

#! /bin/bash

echo "Converting AVI to MPG for $1" #dump in working directory
ffmpeg -i $1 -target ntsc-dvd /dvdtmp/movie.mpg

#move to working directory
cd /dvdtmp

echo "Creating the DVD file structure"
dvdauthor -o dvd -t movie.mpg && echo "Successfully created file structure"

echo "Finalize the structure"
dvdauthor -o dvd -T && echo "File Structure finalized"

echo "Creating the ISO"
mkisofs -dvd-video -o dvd.iso dvd && echo "ISO created successfully"

echo "Burning ISO"
growisofs -dvd-compat -Z /dev/dvd=dvd.iso && echo "DVD has been burned"

echo "...just a little cleaning up..."
rm -R * && echo "Temporary files have been deleted"

echo "Process Complete"

```

---

### Post by aflores3 on 2009-12-17
hatetea,
Thank you for your reply. I have researched tools to burn video to DVD. My favorite of which is DeVeDe. However, I'm looking for a more simple approach. I have a headless media server that shares my entire movie library to every tv in the house (via mythtv/mythvideo). The only downside is that my children like to take dvds to watch in the vehicle on our frequent trips. 

For this application, I dont need all the bells & whistles these authoring/burning programs offer. I just need a quick and easy method to get an xvid to a dvd. I will most often do this by SSH'ing into the machine.

Since I originally posted, I've added the function to eject the dvd upon completion so I can easily see when the disc is ready. Any other ideas?

Also, hatetea, you really should give tea a chance. It truly is delicious :P (we drink southern USA tea here which is essentially sugar-water)

---

### Post by Grenage on 2009-12-17
```
rm -R *
```

You're brave ;)

It's a nice script.

---

### Post by aflores3 on 2009-12-17
> **Grenage said:**
> ```
rm -R *
```

You're brave


I realize this is pretty destructive. I figured since its working in a tmp directory, it should be ok. do you have an alternative way to cleanup these temp files after the iso has been burned?

---

### Post by Grenage on 2009-12-17
I always specify the full path, but I've made the one and only rm mistake I want to. :)

---

### Post by aflores3 on 2009-12-17
> **Grenage said:**
> I always specify the full path, but I've made the one and only rm mistake I want to. :)
Thanks for the advice. 

I know it wont bring your files back, but you can continue knowing that you helped me avoid rm'ing my entire drive :D

---

### Post by Grenage on 2009-12-17
It's unlikely that it will happen, but better safe than sorry!

---

### Post by aflores3 on 2009-12-17
OK,
In case anyone was is watching, I've made a few changes. I'm testing them now:

[LIST=1]
[*]I've Changed the variable to $MOVIE
[*]I put $MOVIE in double quotes in my ffmpeg command in case the original filename has spaces etc. 
[*]After dvdauthor completes, I remove the converted mpg to save space (tell me if this is foolish)
[*]After the ISO is created, it checks if there is a blank in the dvd burner[LIST=2]
[*]if no, moves a copy to the desktop so i can easily see it and remember to burn it later
[*]if yes, it burns
[/LIST]
[*]cleans up a little more safely thanks to **Grenage**
[/LIST]


```

#! /bin/bash

MOVIE="$1"

echo "Converting AVI to MPG for $MOVIE" #dump in working directory
ffmpeg -v 1 -i "$MOVIE" -target ntsc-dvd /dvdtmp/movie.mpg
#exit [n]

#move to working directory
cd /dvdtmp

echo "Creating the DVD file structure"
dvdauthor -o dvd -t movie.mpg && echo "Successfully created file structure"

echo "Finalize the structure"
dvdauthor -o dvd -T && echo "File Structure finalized"

rm movie.mpg #save space ?

echo "Creating the ISO"
mkisofs -dvd-video -o dvd.iso dvd && echo "ISO created successfully"

#check if a blank is in the burner
if ! hal-device | grep volume_empty_cd_r;

then

	#how do i get this to remove the original extension & replace with .iso? now it just appends, which is fine but ugly
        mv dvd.iso ~/Desktop/"$MOVIE".iso
	echo "$MOVIE.iso has been placed on your desktop to burn later"

else

	echo "Burning ISO"
	growisofs -dvd-compat -Z /dev/dvd=dvd.iso && eject /dev/dvd && echo "DVD has been burned"

	echo "$MOVIE has been burned"

fi

echo "...just a little cleaning up..."
rm -R /home/abel/dvdtmp/* && echo "Temporary files have been deleted"
echo "Process Complete"

```

---

