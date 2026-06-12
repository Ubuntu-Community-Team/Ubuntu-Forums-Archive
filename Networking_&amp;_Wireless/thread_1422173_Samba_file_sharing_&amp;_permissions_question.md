---
title: "Samba file sharing &amp; permissions question"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by darthrax on 2010-03-05
Hi all,

I have to do a setup for an office where they are migrating from an unorganized data setup to an organized one. Their existing data is organized into 7 different parent categories and then there are various sub-folders in each one for different projects (eg: Institution/projectname/data etc.). Their new organization scheme basically carries forward the existing structure verbatim but new projects are placed into organized directories (eg: 4001 - project name/../../data) which are created by a script. So they have the following requirements.

1. All parent directories must be read & list to allowed users. Only a script written to create the organized directory structure will create new folders in the parents.

2. All old project sub-folders are to be read & list to allowed users. (Basically their state is frozen)

3. All current project sub-folders are to be frozen and only the working directories should be accessible to allowed users.

4. For all new project folders created, only the last folder in the hierarchy is to be writable. All other folders are read & list only.

5. No user but the admin will have delete rights. They can create, modify and save but not delete. (I don't really know if this is possible.)

6. Also, i would like to know if its possible for two users to be working on the same excel file (different sheets to avoid overlap) without that file being in read-only mode for either.

Their are approximately 30 client machines connecting to the server. The existing situation is this:

All files and folders are owned by the admin user & group 'server'. They all have 2777 permissions. The shares all have guest access so all clients connect with user 'nobody' and group 'nogroup' and do their work. This has led to a complete mish mash of file permissions as all new files are created with nobody:nogroup. When i reset the permissions back to server:server, i also reset the permissions to 3777 so no-one could delete the existing data. This led to users not being able to save their work and being able to delete all new files created from that point on. So i reset the permissions back to 2777 and all was well.

i created a new share called testing to try out the new permissions scheme. I also created a user 'mnk' to eliminate nobody:nogroup. I have set the folder permissions to server:mnk 3750 and last folders to server:mnk 3770. I created a few test folders with the project creator script and after logging in with the mnk user, i am still able to create and delete files and folders anywhere i want. What am i doing wrong? the user mnk is not part of any other group. The user server is not part of group mnk. the configuration for the testing share is:

```
[testing]
	writeable = yes
	wide links = no
	path = /media/data/testing
	force directory mode = 750
	force group = mnk
	force create mode = 770
	revalidate = yes
	force user = server
	comment = permissions testing share
	valid users = @mnk,@server
	create mode = 770
	directory mode = 770
```

I know that this is a long and confusing post. I know that part of what i need to accomplish can be done, i just wondered if theres a better way to do it than to go individually with each folder. 

Thanks in advance.

---

### Post by darthrax on 2010-03-06
bump

---

