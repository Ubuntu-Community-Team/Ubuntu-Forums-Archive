---
title: "Audacity refuses to open directory or file"
date: 2022-11-25
forum: Multimedia Software
---

### Post by Robbyx on 2022-11-25
What am I doing wrong?

I have a mp3 file that I want to edit in Audacity so that I can save just a portion of it to a new file. 

File---> open ---> new ---> open directory (by browsing to the directory)

Error message: Could not read the contents of YVideos (this contains the mp3 )
                          Permission denied

NB:
Permissions as shown  by Nautilus:

Owner: Me,  access: create and delete files
Others: access files 

Using Ubuntu 20.04

---

### Post by #&amp;thj^% on 2022-11-25
Are you opposed to installing the .deb version?
```
apt policy audacity
audacity:
  Installed: (none)
  Candidate: 3.2.0+dfsg-1
  Version table:
     3.2.0+dfsg-1 500
        500 http://us.archive.ubuntu.com/ubuntu devel/universe amd64 Packages


```
EDIT here's the overhead:
```
================================================================================
 Installing                                                                     
================================================================================
  Package:                  Version:                                     Size:  
  audacity                  3.2.0+dfsg-1                                5.4 MB  
  audacity-data             3.2.0+dfsg-1                                2.6 MB  
  libflac++6v5              1.3.4-2                                      31 KB  
  libpcre2-32-0             10.40-1ubuntu1                              197 KB  
  libportaudio2             19.6.0-1.2                                   69 KB  
  libportmidi0              1:217-6.1                                    19 KB  
  libportsmf0v5             0.1~svn20101010-6ubuntu1                     61 KB  
  libsbsms10                2.3.0-1                                     113 KB  
  libsoundtouch1            2.3.1+ds1-1                                  38 KB  
  libsuil-0-0               0.10.18-1                                    26 KB  
  libvamp-hostsdk3v5        2.10.0-3                                     89 KB  
  libwxbase3.2-0            3.2.0+dfsg-2                                871 KB  
  libwxgtk3.2-0             3.2.0+dfsg-2                                4.6 MB  
                                                                                
================================================================================
 Suggested, Will Not Be Installed                                               
================================================================================
  Package:                  Version:                                     Size:  
  wah-plugins               0.1.0-5build1                                 7 KB  
                                                                                
================================================================================
 Summary                                                                        
================================================================================
 Install 13 Packages                                                            
                                                                                
 Total download size  14.1 MB   
 Disk space required  57.3 MB   
                                
Do you want to continue? [Y/n] 


```

---

### Post by Robbyx on 2022-11-25
I am happy to install the deb version. I just looked in Synaptic. Its latest version is 2.3.3-1build.

Where can I find a later deb version as you sight  3.2 in your comment.

---

### Post by DVoid on 2022-11-25
If you've installed the snap version, you should be able to give it mounted storage permissions in the snap or ubuntu store. I can't remember exactly where for 20.04 sorry. But go the the software tool, find the app, and it will be in file permissions somewhere there.

---

### Post by Dennis N on 2022-11-25
Apparently you have the snap version, which is 3.1.3 at this time. Since it's already installed, why not just copy the mp3 file to a location in your home directory. Then your snap version will be able to open and edit the file. And you don't need the latest version for what you intend to do.

---

### Post by #&amp;thj^% on 2022-11-25
> **Robbyx said:**
> I am happy to install the deb version. I just looked in Synaptic. Its latest version is 2.3.3-1build.

Where can I find a later deb version as you sight  3.2 in your comment.
Sorry that version is in Lunar Development 23.04.
> **Dennis N said:**
> Apparently you have the snap version, which is 3.1.3 at this time. Since it's already installed, why not just copy the mp3 file to a location in your home directory. Then your snap version will be able to open and edit the file. And you don't need the latest version for what you intend to do.
+1

---

### Post by Robbyx on 2022-11-26
I have copied the file into the home/ music  directory and have the file loaded into audacity. 
I tried to access the manual but can not get beyond:


Access denied Error code 1020

You cannot access manual.audacityteam.org. Refresh the page or contact the site owner to request access.

For what I am trying to do is there a simpler  program? I know the start and stop time of the extract and do not mind a CLI.

---

### Post by #&amp;thj^% on 2022-11-26
> **Robbyx said:**
> I have copied the file into the home/ music  directory and have the file loaded into audacity. 
I tried to access the manual but can not get beyond:


Access denied Error code 1020

You cannot access manual.audacityteam.org. Refresh the page or contact the site owner to request access.

For what I am trying to do is there a simpler  program? I know the start and stop time of the extract and do not mind a CLI.

Robbyx this will give you a smile: [https://forum.audacityteam.org/viewtopic.php?t=111412](https://forum.audacityteam.org/viewtopic.php?t=111412)
The .deb file should be just fine for what your after.

---

### Post by Robbyx on 2022-11-26
I am not able to access the Audacity forum. I get the error message I posted at #8

---

### Post by #&amp;thj^% on 2022-11-26
> **Robbyx said:**
> I am not able to access the Audacity forum. I get the error message I posted at #8
Whenever I try to access the website [www.audacityteam.org](www.audacityteam.org), I receive the following message: Error 1020 Access denied.

Can you help me to resolve this situation?

Thank you very much!



OK, that's where the smile come in IE:
Poster wrote Dear Audacity Team,

It goes on to report that the address has been blocked due to spam!!! Robbyx have you been spamming Audacity...:lolflag:
> I'll pass this on to our system administrator.

What's happening is that Cloudflare (which protects the Audacity websites against malicious attacks) is blocking your access for some reason. Our system administrator should be able to determine the reason from the information that you have provided.

**_I notice that your IP address appears on some spam blacklists, which is probably why Cloudflare is blocking[_**
You have to get a hold them @"https://forum.audacityteam.org/memberlist.php?mode=contactadmin" to get your IP listed again as good.

---

### Post by DVoid on 2022-11-26
Hi Robbyx,
If you're happy with a CLI try

ffmpeg -ss HH:MM:SS -t XX -i input.mp3 output.mp3

where HH:MM:SS is the start time, e.g. 00:00:05 to start 5 seconds into the song,
XX is the duration to extract, eg. 10 seconds from the starting point you defined,
and input.mp3 and output.mp3 are the input and output filenames you wish to use.

Hope that helps/

---

### Post by Robbyx on 2022-11-27
> **DVoid said:**
> Hi Robbyx,
If you're happy with a CLI try

ffmpeg -ss HH:MM:SS -t XX -i input.mp3 output.mp3

where HH:MM:SS is the start time, e.g. 00:00:05 to start 5 seconds into the song,
XX is the duration to extract, eg. 10 seconds from the starting point you defined,
and input.mp3 and output.mp3 are the input and output filenames you wish to use.

Hope that helps/

Thank you for pointing to ffmpeg. Your example made it hugely easier for me to extract a portion of recording than using the various GUI programs that I have  tried unsuccessfully to use for this action.

I did struggle with referencing the input file in the command line. The program kept misunderstanding the length of the url because I had named  the file with spaces between the words.

I tried putting the file name in inverted commas, but that did not work. In the end I renamed the directory and the source file by replacing spaces with hyphens. 

Do you know if it is possible to use ffmpeg to point to file names with spaces separating the words in the name?

---

### Post by #&amp;thj^% on 2022-11-27
> **Robbyx said:**
> Do you know if it is possible to use ffmpeg to point to file names with spaces separating the words in the name?

If you happen to have spaces in your file name, just quote them:
```

EXAMPLE ONLY
ffmpeg -i "my input.mp3 file.mp3"
```

If your In a URL, a space cannot be there. Most probably you have to replace every single space with a %20, so that you get:
```

ffmpeg -i http://myurl.com/my%20video%20file.mov
```
Remember always filename with spaces inside quotes** ""**
Sorry I did not see where you would accept "CLI"
Did you ever get sorted with the Audacity URL ??

---

### Post by DVoid on 2022-11-28
> **Robbyx said:**
> Thank you for pointing to ffmpeg. Your example made it hugely easier for me to extract a portion of recording than using the various GUI programs that I have  tried unsuccessfully to use for this action.

I did struggle with referencing the input file in the command line. The program kept misunderstanding the length of the url because I had named  the file with spaces between the words.

I tried putting the file name in inverted commas, but that did not work. In the end I renamed the directory and the source file by replacing spaces with hyphens. 

Do you know if it is possible to use ffmpeg to point to file names with spaces separating the words in the name?

Hi Robby, no problem, glad to help. Forgot to mention that partial seconds can be used in the time codes as well: e.g. HH:MM:SS.m 

1fallen has quite nicely indicated how to handle spaces in your file names.

---

