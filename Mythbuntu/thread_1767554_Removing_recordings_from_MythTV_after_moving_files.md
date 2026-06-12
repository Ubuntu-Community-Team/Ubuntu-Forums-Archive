---
title: "Removing recordings from MythTV after moving files"
date: 2011-05-25
forum: Mythbuntu
---

### Post by PatrickD-52761 on 2011-05-25
Hello everyone,

Here's what I've done.  I have an 80GB drive, which is my main hard drive, and a 320GB external USB Drive.  I moved all of my recorded tv shows from the 80GB drive to the USB drive, and want to remove them from the MythTV Media Library.  

As an alternative, I would like to change the recording location to the USB drive, so I don't have to worry about this in the future.

So, my questions are 
1.  How do I remove the recordings from my media library?
2.  If I change the recording location before doing #1, will the recordings show up twice (or will they open properly)?
3.  If I remove the recordings from the media library, and then change the location to the USB Drive, will the recording show up again?

Have a great day:)
Patrick.

---

### Post by nickrout on 2011-05-26
1. make a subdirectory on your external drive (like /media/usbdrive/recordings)

2. Move the recordings into that directory

3. add that directory as a storage dirctory 9thats in the mythtv-setup application).

4. end of story.

---

### Post by PatrickD-52761 on 2011-05-26
> **nickrout said:**
> 1. make a subdirectory on your external drive (like /media/usbdrive/recordings)

2. Move the recordings into that directory

3. add that directory as a storage dirctory 9thats in the mythtv-setup application).

4. end of story.

I've already done #1 and #2. So, when I add the directory, will the recordings show up in my Media Library twice (as they still show up there now--although I can't watch them)?

Thanks for the assistance :)
Patrick.

---

### Post by PatrickD-52761 on 2011-09-03
I'm marking this as solved due to finding some answers in the MythTalks forum.  Essentially what this boils down to is that the drive must be formatted with a filesystem which accepts Unix-style permissions.  My drive was formatted as NTFS, since I was dual-booting between Mythbuntu and Windows 7.  

What I had to do is resize the partition down as low as I could, create a new partition (I formatted it as ext4), move all of the recordings over that I could (since it wasn't big enough for all of them at one time), rinse and repeat...

I'm on the final resize/move right now, and it has about 4 hours left to go.  Then I'll copy the rest of the files over, and most likely delete the NTFS partition altogether (or maybe leave about a 20GB size for use with Windows).  

After creating the second partition (the ext4 one), I used the terminal and put 
```

cd /media
ls -l
sudo chmod 777 recordings
ls -l

```(note that your chmod will be whatever label you gave the partition), and added that partition into MythTV Backend under storage directories. When I'm finished resizing everything, I will verify that everything works correctly (which it should since all users/groups have total access to the partition now).

You can find the thread at [http://www.mythtvtalk.com/questions-about-properly-moving-recordings-mythtv-15025/]("http://www.mythtvtalk.com/questions-about-properly-moving-recordings-mythtv-15025/").

Have a great day, and thanks for helping :)
Patrick.

---

