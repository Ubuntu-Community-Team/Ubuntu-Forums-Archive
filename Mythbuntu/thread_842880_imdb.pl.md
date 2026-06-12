---
title: "imdb.pl"
date: 2008-06-27
forum: Mythbuntu
---

### Post by Stevieo85 on 2008-06-27
Hi All,

I am having a few problems with imdb.pl. This downloads the the data from the imdb successfully but it will not download the movie posters.

I have set up the directory for the movie posters and set the setting in mythweb/settings/mythweb for the VideoArtworkDir: and the directory has 777 permissions

Cheers,

Steven

---

### Post by anand on 2008-06-27
Do you see any error messages when calling imdb.pl from the command line?

You can do something like this.  The 1st command will tell you the IMDB # that you'll use in the second command:

/usr/share/mythtv/mythvideo/scripts/imdb.pl -d -M Airplane
/usr/share/mythtv/mythvideo/scripts/imdb.pl -d -P 0080339

I don't think this script will actually try to download the poster but at least you can see if there is some issue with the script figuring out the right URL to grab it from.

---

### Post by Stevieo85 on 2008-06-27
Thanks for the reply, I see no issues running it from command line and when i request the poster it finds the location ok as well. The script works from MythVideo in the video manager just not from mythweb.

---

### Post by toorima on 2008-06-28
if its only mythweb that doesn't work for you, try this

cd /var/www/mythweb/data/
sudo rm ./video
sudo ln -s <Path to Videos> ./video
sudo rm ./video_covers
sudo ln -s <Path to Video Covers> ./video_covers

---

