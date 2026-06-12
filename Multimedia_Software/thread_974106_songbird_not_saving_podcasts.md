---
title: "songbird not saving podcasts"
date: 2008-11-07
forum: Multimedia Software
---

### Post by hachel on 2008-11-07
hi,
when i add a pocast to songbird (0.7 and 1.0RC), it specify a folder to save to (home/user(hachel)/music/podcast), and it starts downloading them.
But at 99% switching to 100% it sais "failed", like it was downloading to some temp-folder and had trouble actually saving it to the folder specified as the destinationfolder.
I think that might be due to some permission-error?

I "installed" songbird by downloading the tar-file, then I unpacked it, copied it to /opt/songbird and changed permission on it to me. everything else works.

Maybe there is a way to see where songbird is actually downloading to? cause nothing appears in the podcastfolder during the download.

cheers,

hachel

PS: i can download files with the build-in browser

---

### Post by izzy200198 on 2008-12-06
Hello,

Im having the exact same problem using version 1.0 with Intrepid. it says 99% failed and the podcasts are not in the music folder. however they all downloaded and are somewhere on my drive because i can play them. and they are hogging up my drive space. does anyone know where to find the downloaded podcasts so i can delete them and recover my hard drive space?

---

### Post by achinton on 2008-12-08
I also have this problem, and have had for several versions of Songbird so far. It's an odd bug, because other download functions within Songbird work fine, it's just the podcast downloading that doesn't.

izzy200198, are you sure the files are being saved somewhere? Could Songbird not just be streaming the files from the internet to play them?

---

### Post by reverend_nerd on 2008-12-27
I've got the same problem with my Mint 6 Felicia (which is a Ubuntu-based distro).
I just found out where the downloaded and failed podcasts are kept, in the /tmp/Songbird directory.

hope I could be of any help :)

---

### Post by chzumbrunnen on 2009-03-30
This thread seems a few monthes old and since new versions of songbird came out but still I have this very same problem. Did someone find a solution yet?
I would appreciate any hint since I'd like to use songbird but this bug makes it almost unusable for me.

---

### Post by mkkohls on 2009-05-17
The podcast support in songbird is not finished. Its on the roadmap for the august release to have full podcast support. 

I've also been unable to find a solution and assume I will just have to wait for them to add the support.

---

### Post by arcane14 on 2009-05-18
I'm glad to hear it's on the radar. It's the most important missing piece. For now I'm settling for listening right from Google Reader, which gets the job done.

---

