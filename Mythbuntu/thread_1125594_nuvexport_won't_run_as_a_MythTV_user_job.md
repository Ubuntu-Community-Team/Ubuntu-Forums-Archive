---
title: "nuvexport won't run as a MythTV user job"
date: 2009-04-14
forum: Mythbuntu
---

### Post by Bloodrule on 2009-04-14
I can run nuvexport flawlessly from the command line, but if I set it up as a user job, MythTV reports queued/running/finished ie success but there is no converted file to be found.  I have set all necessary permissions.

Any clues?

---

### Post by klc5555 on 2009-04-15
> **Bloodrule said:**
> I can run nuvexport flawlessly from the command line, but if I set it up as a user job, MythTV reports queued/running/finished ie success but there is no converted file to be found.  I have set all necessary permissions.

Any clues?

Just a guess. When you run nuvexport from a prompt, you're running it as you. In the job queue, the user "mythtv" is running it. nuvexport may be set up to drop the end file into a directory that you have write authority to, but the user "mythtv" doesn't (for example, your home directory)

---

### Post by Bloodrule on 2009-04-15
Good thought - but not the answer unfortunately.  Mythtv is the owner of the directory defined in nuvexportrc - in this case /var/lib/mythtv/recordings/

Appreciate your answer, but still mysteriously non-existent files after MythTV reports successful conversion.

---

### Post by klc5555 on 2009-04-15
> **Bloodrule said:**
> Good thought - but not the answer unfortunately.  Mythtv is the owner of the directory defined in nuvexportrc - in this case /var/lib/mythtv/recordings/

Appreciate your answer, but still mysteriously non-existent files after MythTV reports successful conversion.

Well, I suppose the next step would be to see whether any mysterious messages get left in the mythbackend.log when the job runs (or doesn't).

---

### Post by Bloodrule on 2009-04-16
Thanks for the tip - here's the relevant (I think) error message from mythbackend.log:

No config found; attempting to find mythbackend via UPnP.
No backends found.  Please copy /home/mythtv/.mythtv/config.xml from a working MythTV installation instead.
Compilation failed in require at /usr/bin/nuvexport-xvid line 36.
BEGIN failed--compilation aborted at /usr/bin/nuvexport-xvid line 36.

My installation is a "vanilla" Mythbuntu 8.10 frontend/backend so I am not sure why these messages are occurring.  Any comments appreciated.

---

### Post by Bloodrule on 2009-04-16
Thanks to the leads you gave me, problem SOLVED!

Two steps needed:

copied config.xml from /home/myhomedir/.mythtv/ to home/mythtv/.mythtv/

sudo apt-get install ncurses-term

Solution at [http://ubuntuforums.org/showthread.php?t=346778&page=20](http://ubuntuforums.org/showthread.php?t=346778&page=20)

Thanks, I would never have got there without your help.

---

### Post by kwisher on 2009-09-07
Hello,

The tip in the previous post has gotten me further along but I receive the following when issuing the following command:

```
nuvexport-dvd --ffmpeg --nice 19 --input="%FILE%"
```

error:

```
Loading MythTV recording info.
9% 
Input filename does not match the MythTV recording name format
and no matching file could be found in the MythTV database.
Please reference only files in your active MythTV video directory.

Cleaning up temp files.
```

Any help would be greatly appreciated.

---

### Post by SiHa on 2009-09-07
Are you running this from the command line? This command will only work as a user job, where Myth passes the filename in the %FILE% parameter.

To prove it works in isolation, have you tried the above from the commandline but giving it the name of a file from the recordings directory instead. Or you can run it without a "--input=...", and Nuvexport will list all available recordings in the database to choose from (well it did last time I used it anyway).

---

### Post by kwisher on 2009-09-08
> **SiHa said:**
> Are you running this from the command line? This command will only work as a user job, where Myth passes the filename in the %FILE% parameter.

To prove it works in isolation, have you tried the above from the commandline but giving it the name of a file from the recordings directory instead. Or you can run it without a "--input=...", and Nuvexport will list all available recordings in the database to choose from (well it did last time I used it anyway).

SiHa,

Thanks for the response and you are correct. When I remove the input parameter from the terminal command it works as expected.

So I added the full command as a user job and gave it a descriptive name. The new user job shows up in the MythWeb interface. So I started the new user job on a recording that was captured & stored on my secondary backend. Now I cannot find the new transcoded file. Where is the new file being stored?

TIA

---

