---
title: "Elisa: The Missing Folders Mystery"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by scott_g on 2007-06-11
Hi,

I have the Elisa Media Center installed, and really enjoy using it, but certain folders do not appear.  Here is my folder structure of My Pictures:

My Pictures/ Folders of Names / Folders of events from that person.

Eg: My Pictures/ Fred / Graduation Dinner

However, sometimes, on the 3rd level (Graduation Dinner), some folders are missing; I can see them in the file browser (there should be 15 folders), yet they do not appear in Elisa (only two show up).  If I change the configuration file to show only the specific 2nd level folder (Fred), three sub folders show up, yet they are a different three than previously.

Any ideas about how I can get the rest of the folders to appear?

If you need any clarification, or want me to post something, just ask.

Thanks a lot,
Scott

---

### Post by dfreer on 2007-06-11
Try checking the permissions of those folders. They should be 755 (or rwxr-xr-x) in order for everyone to be able to read and browse the folders.

EDIT: Also, it may not show the folders if there are no compatible files found in them (for example, if it has .svg files and your program doesn't support .svg files). Just an idea.

---

### Post by scott_g on 2007-06-11
Thanks, I did a sudo chmod 755 * -R to the main pictures folder, but it didnt seem to help :(.

I think they are compatible, all of the 3rd level folders have several .jpg files in them; funny part is that it shows thumbnail previews from the 3rd level subfolders (which have disappeared) when viewing the 2nd level folder.

Thanks again,
Scott

---

### Post by dfreer on 2007-06-11
Probably a bug in the software then, I'm guessing. You might want to let the makers of Elisa know your specific problem, they can probably help you out the best. 

On a side note, how do you like elisa, specifically compared to windows media center?

---

### Post by scott_g on 2007-06-11
I like Elisa a lot, once its configured (there should be an easier way other than editing the config file), and if you don't need to view .wmv's, then its great.  The only thing I miss is how Windows MC lays out music files; I find it slow to scroll in between songs.

In all, I feel it is an excellent replacement.

I might do some searching for an Elisa forum, or send the developers an email.

Thanks a lot for the advice/help,
Scott

---

### Post by scott_g on 2007-06-11
I may have found why this is happening.  I found out by reading here: [http://servers.linux.com/article.pl?sid=07/05/04/1955225&tid=39](http://servers.linux.com/article.pl?sid=07/05/04/1955225&tid=39) that elisa is limited to 100 items per menu; the folders I was looking in had 400+ items (I have a lot of pictures); it must have listed them in alphabetical order or something and only displayed the first 100.  According to the article, this restriction will be removied in the 0.2 release, incase anyone else had this problem.

Scott

---

### Post by dfreer on 2007-06-11
Good to know, thanks!

---

