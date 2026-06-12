---
title: "How to view multi-part videos"
date: 2009-10-01
forum: Multimedia Software
---

### Post by cstoh on 2009-10-01
Hello to experts here. I downloaded a video that came in four parts and have file names such as "6644.avi.001", "6644.avi.002", "6644.avi.003" and "6644.avi.004". I find that the system only recognises the first file "6644.avi.001" as a video and am able to play it in Movie Player. The other files are not recognised at all and so cannot be viewed. Please help. Thanks alot.

---

### Post by cor2y on 2009-10-01
you need to join the files together back into the single avi file.
via the terminal
```
 cat 6644.avi.001 6644.avi.002 6644.avi.003 6644.avi.004 > 6644.avi
```I believe 7z can do this as well via the terminal
```
 sudo apt-get install 7z
``````
 7z x 6644.avi.001
```Finally if you must have a gui then the java version of hjsplit or the linux version  can join and split files 
[http://www.freebyte.com/hjsplit/#linux](http://www.freebyte.com/hjsplit/#linux)
[http://www.freebyte.com/hjsplit/#ljava](http://www.freebyte.com/hjsplit/#ljava)

---

### Post by cstoh on 2009-10-03
> **cor2y said:**
> you need to join the files together back into the single avi file.
via the terminal
```
 cat 6644.avi.001 6644.avi.002 6644.avi.003 6644.avi.004 > 6644.avi
```I believe 7z can do this as well via the terminal
```
 sudo apt-get install 7z
``````
 7z x 6644.avi.001
```Finally if you must have a gui then the java version of hjsplit or the linux version  can join and split files 
[http://www.freebyte.com/hjsplit/#linux](http://www.freebyte.com/hjsplit/#linux)
[http://www.freebyte.com/hjsplit/#ljava](http://www.freebyte.com/hjsplit/#ljava)

Hi there, I used your first solution, I got a terminal window and after typing "sudo su" and keying the password I keyed in "cat 6644.avi.001 6644.avi.002 6644.avi.003 6644.avi.004 > 6644.avi".
The terminal window then becomes a mass of odd characters for a couple of hours. At the end it becomes a window filled with "9:c62" and the cursor waiting for input. I hit Enter then there is a long sequence of error messages "9: command could not be found", "c62 command could not be found". Then finally it stops and wait for inputs. What do I type?

---

### Post by cotcot on 2009-10-03
The first solution is without sudo su.
For the second solution sudo su is only needed to install the application 7z. To use the 7z application you do not need sudo su.

---

### Post by cstoh on 2009-10-06
Hello, thanks for your help. I realised my mistake. I did not cut and paste the statement given in the reply with the solution. I typed in instead and I missed the ">" before the "6644.avi" filename. 
No wonder I was getting a scrolling terminal screen with weird symbols. In effect I was asking "CAT" to join a list of files and not giving an output filename. Thus it just dumped its output to the standard output device, which is the screen. To make matters worse, the last file is non existent. Thus it was waiting for more inputs. Also the screen, being a slow device, took hours to display the output.

Now that I did it correctly, it took only a few minutes and I have my file.

Thanks again

---

