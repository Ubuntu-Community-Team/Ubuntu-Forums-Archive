---
title: "help restore f-spot database Please"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by shane2peru on 2008-02-24
Ok, this may be a bit technical.  I had to re-install and setup my Ubuntu, so I changed my username.  Now when I restored my database from my backup file in **.gnome2/f-spot/photos.db**  I copied that file  back to my new home directory as well as my **Photos** folder.  Now when I open f-spot, my photos don't show up.  There is a space, and all the photo albums are there, however no actual picture.  I'm about 90% sure that somewhere in the database folder is hard coded my old user name.  When I click on **View -> Meta Data Browser**  it gives me to old location with the old user name.    Does anyone have any idea how to fix this?  Thanks.

Shane

---

### Post by Sam Lars on 2008-02-25
Have you tried copying the whole F-spot directory (is there anything else in there)?

---

### Post by shane2peru on 2008-02-25
Sam Lars,

Thanks, however I'm sure it has to do with the changing of the user name.  The only file needed is the photos.db file.  I can't really transfer everything, because I upgraded to 64bit, and the config files tend to mess up the way the programs work.  Found that out the hard way.  

Shane

---

### Post by detoj on 2008-05-02
Hi Shane,

Did you ever figure out how to get your photos to appear back in F-Spot?  I'm now in exactly the same situation as your were after upgrading to Hardy.  The directory my photos used to be in had a name change, and now the photos don't appear in the program, although the tags and everything are still there.  If you ended up finding a relatively easy way of fixing this, please pass it along.  Thanks!

Dan

---

### Post by shane2peru on 2008-05-02
> **detoj said:**
> Hi Shane,

Did you ever figure out how to get your photos to appear back in F-Spot?  I'm now in exactly the same situation as your were after upgrading to Hardy.  The directory my photos used to be in had a name change, and now the photos don't appear in the program, although the tags and everything are still there.  If you ended up finding a relatively easy way of fixing this, please pass it along.  Thanks!

Dan

Dan,

Hmm, I don't think I ever did find an answer.  I added a new user with the same name and moved all my files over.  And then re-installed again with hardy, and have abandoned f-Spot and am sticking with Picasa.  I did find that a file contained the directory, and if that file was edited it would point to the proper place, but I don't remember what the file was, or was that Rhythmbox, ahh, I just don't remember now.  Hope someone has an answer for ya.

Shane

---

### Post by russo on 2008-05-19
Hi

I have a possible solution for you.
0. Open a terminal
1. Install sqlite 
**  sudo apt-get install sqlite**
2. Make a backup copy of your database
**  cp ~/.gnome2/f-spot/photos.db ~/.gnome2/f-spot/photos.db.bak**
3. Export your photos table
**  sqlite ~/.gnome2/f-spot/photos.db ".dump photos" > photos.sql**
4. Edit the file with gedit
**  gedit photos.sql**
5. Delete the second line of the photos.sql file
**  ...CREATE TABLE photos...**
6. Replace that line with
**  DELETE FROM photos;**
7. You will see that the path for your pictures points to your old $HOME. Replace the path of your pictures in the file with your new HOME
8. Save the file and quit gedit
9. Re-import the file
**  sqlite ~/.gnome2/f-spot/photos.db < photos.sql**
10. Launch f-spot. You should be an happy man now ;-)
11. If it all worked remove the backup of your database and the sql file
**  rm ~/.gnome2/f-spot/photos.db.bak**
**  rm photos.sql**

Hope this helps

---

### Post by russo on 2008-05-19
double post

---

