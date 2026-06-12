---
title: "cheese webcam cluttervideosink"
date: 2016-03-04
forum: Multimedia Software
---

### Post by goodstuff9 on 2016-03-04
ubuntu 15.10

Cheese 3.16.1

When I start Cheese, I get this error message:  

"One or more gstreamer elements are missing cluttervideosink"

I tried following the suggested workarounds found here:  

[http://askubuntu.com/questions/450804/cheese-do-not-start-due-gstreamer-elements-are-missing-cluttervideosink]("http://askubuntu.com/questions/450804/cheese-do-not-start-due-gstreamer-elements-are-missing-cluttervideosink")

and here:  

[http://askubuntu.com/questions/461045/unable-to-start-webcam-via-cheese-cluttervideosink-missing]("http://askubuntu.com/questions/461045/unable-to-start-webcam-via-cheese-cluttervideosink-missing")

Those steps won't work for me because at the step that says to remove the folder ~/.cache/gstreamer1.0, as soon as I remove it, it somehow mysteriously recreates itself.  I have no idea why that happens, nor do I know how to make Cheese work.  Any ideas?  Thanks.

---

### Post by QDR06VV9 on 2016-03-04
1.remove clutter-gst package
2.remove ~/.cache/gstreamer-1.0/
3.will work
The only problem will be...It will want to remove or uninstall totem because it depends on clutter-gst  
Good Luck regards

---

### Post by goodstuff9 on 2016-03-04
Thanks for the quick reply, but......

As I wrote in my original posting, I am unable to do step #2.  As soon as I remove it, it somehow mysteriously recreates itself.  As in, within about 1.5 seconds.

---

### Post by QDR06VV9 on 2016-03-04
That is because you have not 
1.remove clutter-gst package..Uninstall it

---

### Post by goodstuff9 on 2016-03-04
Thank you again.  

Sorry, but I looked in Syanptic.  I do not have a package called "clutter-gst" installed.  

I do have packages called "gir1.2-clutter-gst-1.0", "gir1.2-clutter-gst-2.0", and "libclutter-gst-2.0-dev", but no package called simply "clutter-gst".  

Any other ideas?

---

### Post by QDR06VV9 on 2016-03-04
Must be diferent in 14.04
What is the output of this in the terminal
```
sudo apt-get -s autoremove libclutter-gst-2.0-dev
```

This will just run a dry command it will not remove anything it will just show what will be removed

---

### Post by goodstuff9 on 2016-03-04
ok, here is the output:  

main8@lappy8:~$ sudo apt-get -s autoremove libclutter-gst-2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-clutter-gst-2.0 gir1.2-evince-3.0 gir1.2-ges-1.0 gromit
  gstreamer1.0-gnonlin libclutter-gst-2.0-dev libges-1.0-0 libgjs0e
  libjs-jquery-ui libmozjs-24-0v5 libmusicbrainz5-2 libmusicbrainz5cc2v5
  python-matplotlib-data python3-gst-1.0 python3-matplotlib python3-nose
  python3-numpy
0 upgraded, 0 newly installed, 17 to remove and 47 not upgraded.
Remv libclutter-gst-2.0-dev [2.0.16-1]
Remv gir1.2-clutter-gst-2.0 [2.0.16-1]
Remv gir1.2-evince-3.0 [3.16.1-0ubuntu1]
Remv gir1.2-ges-1.0 [1.4.0-2]
Remv gromit [20041213-9]
Remv libges-1.0-0 [1.4.0-2]
Remv gstreamer1.0-gnonlin [1.4.0-2]
Remv libgjs0e [1.43.3-2build1]
Remv python3-matplotlib [1.4.2-3.1ubuntu1]
Remv libjs-jquery-ui [1.10.1+dfsg-1]
Remv libmozjs-24-0v5 [24.2.0-3ubuntu1]
Remv libmusicbrainz5-2 [5.1.0+git20150707-5]
Remv libmusicbrainz5cc2v5 [5.1.0+git20150707-5]
Remv python-matplotlib-data [1.4.2-3.1ubuntu1]
Remv python3-gst-1.0 [1.4.0-2build1]
Remv python3-nose [1.3.6-1]
Remv python3-numpy [1:1.8.2-1ubuntu2]
main8@lappy8:~$

---

### Post by QDR06VV9 on 2016-03-04
Well Yuck!!
That is not going to work... I need to think a bit on this one.
Be back soon
Show me the model of your web cam
```
ls -ltrh /dev/video*

```

---

### Post by goodstuff9 on 2016-03-04
main8@lappy8:~$ ls -ltrh /dev/video*
crw-rw----+ 1 root video 81, 0 Mar  4 13:46 /dev/video0
main8@lappy8:~$ 


I hope that helps!  I know it is a Logitech

---

### Post by QDR06VV9 on 2016-03-04
Ok I have just installed cheese 3.18 on my lenovo lappy and this is the package you need to remove.
"gstreamer1.0-clutter" and then follow the above.
My version of cheese is newer due to 16.04 Xenial (Development)

---

### Post by goodstuff9 on 2016-03-04
No joy.  :(

I removed gstreamer-1.0-clutter (which also removed Cheese).  

I then deleted the directory ~./cache/gstreamer-1.0...... and within milliseconds the directory had recreated itself.

---

### Post by QDR06VV9 on 2016-03-04
How Odd!?!? All files in the .cache directory should be just used for temporarily  caching some contents. If you delete one of them it should be  automatically recreated in the moment they are needed.
I seem to recall some bug on some web cams with willy(15.10) when it was in development.
What is the make and model of your laptop && what kernel version are you running?
For Current running kernel "uname -r"

---

### Post by goodstuff9 on 2016-03-04
main8@lappy8:~$ uname -r
4.2.0-30-generic
main8@lappy8:~$

Lenovo Thinkpad T410

Do you think I'm just stuck?  Do you know, are there other Linux friendly, but more "robust" webcam apps I should look into?

---

### Post by QDR06VV9 on 2016-03-04
Don't know if you are stuck yet? I like challenges like this..
But yes there are other means for web cams: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
I use FFmpeg once in a while.
It might take me a little time to sort this out forgive me..
I will return.

---

### Post by goodstuff9 on 2016-03-04
oh.....  You don't need to ask for any forgiveness!  I am grateful for your help, I've been struggling with this for a LONG time.....

And, in case this helps:  I installed VLC, the webcam works great.

---

### Post by QDR06VV9 on 2016-03-04
> **goodstuff9 said:**
> oh.....  You don't need to ask for any forgiveness!  I am grateful for your help, I've been struggling with this for a LONG time.....

And, in case this helps:  I installed VLC, the webcam works great.
Well very nice then:)..Is it enough to suit your needs?

---

### Post by goodstuff9 on 2016-03-04
Yes, it does work for me.  

The only thing nagging me is:  If Cheese won't work, is that simply a Cheese problem?  Or, is it a symptom of some more fundamental problem with my Ubuntu installation?  Thoughts on that?

---

### Post by QDR06VV9 on 2016-03-04
Probably a combination of cheese and newer software coming in with new release's and software that has not caught up with the rest.. or remaining bugs not fixed yet.
Clear as mud right?:D
EDIT: By the way I do remember having to use the instructions I gave you for Cheese on Wily(15.10) but on Xenial(16.04) it installed and worked as Advertised.
My Laptop is a Lenovo B-570 with the same Web Cam as yours.

---

### Post by goodstuff9 on 2016-03-04
Yeah, it is!  

Hey, thanks for your help with this.  You're a good guy.  Or gal.  

Even though I found a way to get my webcam to work, I couldn't find a way to make Cheese work, so I'm not going to mark this as "solved".

---

### Post by QDR06VV9 on 2016-03-04
Your Welcome..But Definitely a Guy!LOL
And the Not Solved is what I would also do..
Kind Regards

---

### Post by QDR06VV9 on 2016-03-05
Ok I was going through some old files i keep around and ran across this...It helped me early in Wily's Development with cheese on this.
First see if you have guvcview installed.
```
apt-cache policy guvcview
```
And if shows not installed then install it 
```
sudo apt-get install guvcview
```
And I have new information they used a couple of different Web Cams so just to be sure which one you have..Post back the return of this in the terminal.
```
ls /dev/v4l/*
```
Hopefully your will show this model
> usb-Chicony_Electronics_Co.__Ltd._Integrated_Camera-video-index0
Then we can see if Cheese will work correctly.

---

### Post by goodstuff9 on 2016-03-05
I had to install guvcview.  


main8@lappy8:~$ ls /dev/v4l/*
/dev/v4l/by-id:
usb-_Webcam_C170-video-index0

/dev/v4l/by-path:
pci-0000:00:1a.0-usb-0:1.5.2:1.0-video-index0
main8@lappy8:~$

However.....  Cheese got uninstalled.  And, when I try to delete the gstreamer folder, it still reinstalls itself immediately.

---

### Post by QDR06VV9 on 2016-03-05
<Snip just saw this>
Your web cam is a logitech C170 and i think the problem lies there..
The output for mine is as shows
```
 ls /dev/v4l/*
/dev/v4l/by-id:
usb-5618006222B720BG_Lenovo_EasyCamera-video-index0

/dev/v4l/by-path:
pci-0000:00:1a.0-usb-0:1.5:1.0-video-index0

```
Disregard the below with new information I have received..Looks like you are going to have to stick with VLC as your Web Cam App.
[s]Will Cheese re-install?
We will deal with the magic gstreamer folder in a bit..
Oh yeah what is the output of guvcview in the terminal[/s].

---

### Post by goodstuff9 on 2016-03-05
Thanks.....  What makes you suspect the webcam itself is the problem?  I'm not getting that from what you showed.

---

### Post by QDR06VV9 on 2016-03-06
Your web cam is fine, it is just the support that Cheese has ATM.
While I was checking in with other forums there was not much success with your cam and "Cheese" other apps worked as in your case also. 
A couple of friends have sent some links with a work around see these
[http://zoringroup.com/forum/viewtopic.php?f=5&t=8280](http://zoringroup.com/forum/viewtopic.php?f=5&t=8280)

[https://subhadipsblog.wordpress.com/2015/03/15/solved-cheese-webcam-booth-not-displaying-video-from-webcam-in-ubuntu/](https://subhadipsblog.wordpress.com/2015/03/15/solved-cheese-webcam-booth-not-displaying-video-from-webcam-in-ubuntu/)

Then there this bug in Trusty(14.04)
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/1295247](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/1295247)

And another method using Guvcview
[http://mylinuxexplore.blogspot.ca/2012/05/solved-problem-of-logitech-webcams-and.html](http://mylinuxexplore.blogspot.ca/2012/05/solved-problem-of-logitech-webcams-and.html)
Hope this was helpful.
Regards

---

### Post by goodstuff9 on 2016-03-06
Thanks again.  

GTK UVC works great.  

I tried adjusting the resolution on Cheese - Cheese still would not work.  

I think Cheese is hopeless for me, now anyway.  

Hey, one more question, though:  Why do you think it is that I am I unable to delete that gstreamer folder?

---

