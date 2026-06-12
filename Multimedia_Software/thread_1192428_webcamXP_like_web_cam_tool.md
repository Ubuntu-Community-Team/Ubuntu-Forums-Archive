---
title: "webcamXP like web cam tool"
date: 2009-06-20
forum: Multimedia Software
---

### Post by ola on 2009-06-20
Hi! 

I have been using the following webcam tools in windows: 
[LIST]
[*][http://www.webcamxp.com/home.aspx](http://www.webcamxp.com/home.aspx)
[*][http://www.microsoft.com/windowsxp/Downloads/powertoys/Xppowertoys.mspx](http://www.microsoft.com/windowsxp/Downloads/powertoys/Xppowertoys.mspx)
[*][http://www.booru.net/news.html](http://www.booru.net/news.html)
[/LIST]
I've mainly used them to capture images every minute or so to create time-lapse videos.

I'm trying to find a good replacement tool in Linux. Any ideas?

---

### Post by SteveDee on 2009-06-20
> **ola said:**
> Hi! 

I have been using the following webcam tools in windows: 
[LIST]
[*][http://www.webcamxp.com/home.aspx](http://www.webcamxp.com/home.aspx)
[*][http://www.microsoft.com/windowsxp/Downloads/powertoys/Xppowertoys.mspx](http://www.microsoft.com/windowsxp/Downloads/powertoys/Xppowertoys.mspx)
[*][http://www.booru.net/news.html](http://www.booru.net/news.html)
[/LIST]
I've mainly used them to capture images every minute or so to create time-lapse videos.

I'm trying to find a good replacement tool in Linux. Any ideas?

The "motion" application works well. It does not have a GUI so configuration is via a file, and display can be via a web browser. I've used it successfully to capture shots & video of animals moving around my garden at night.

Wiki: [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

---

### Post by arfiansyah on 2012-06-29
please help me,
i have 4 ip camera,.how to configure those ipcamera in **motion**??
how to see the video??
how to display **motion **in our web browser?? i wanna get the video link and then i wanna display it from android..
can u suggest to me what software can i use for this security case??

---

### Post by SteveDee on 2012-06-29
> **arfiansyah said:**
> ...i have 4 ip camera,.how to configure those ipcamera in **motion**??
how to see the video??.....

You don't say how far you have got with this project. Are you just looking for help configuring the IP cameras, or is Kenneth Larvsen's motion application completely new to you?

Motion does not have a user interface, configuration is via one or more configuration files which can be edited via a text editor or via a web interface.

Motion exploits a feature of Firefox, so this is generally the browser to use on a remote computer for a live view of video. However, I also use an Android app called CamBuddy to view video on my phone over my wireless network.

Anyway, if you give me a better idea of your current level of knowledge I'd be happy to try and help you.

---

### Post by arfiansyah on 2012-06-29
> **SteveDee said:**
> You don't say how far you have got with this project. Are you just looking for help configuring the IP cameras, or is Kenneth Larvsen's motion application completely new to you?

Motion does not have a user interface, configuration is via one or more configuration files which can be edited via a text editor or via a web interface.

Motion exploits a feature of Firefox, so this is generally the browser to use on a remote computer for a live view of video. However, I also use an Android app called CamBuddy to view video on my phone over my wireless network.

Anyway, if you give me a better idea of your current level of knowledge I'd be happy to try and help you.

yes,.it's very new to me..
i need help to configure the ip camera in motion and how to configure it from web interface??

---

### Post by SteveDee on 2012-06-29
Assuming you are just starting out, Kenneth Larvsen's motion site is here: [http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome)

Although you want to use motion with 4 IP cameras, I suggest you start with one, check that everything is working properly, and then progress to adding the other three.

Once you have installed motion, the first thing to do is copy the motion.conf file to your home directory on the host computer. For example copy /etc/motion/motion.conf to /home/{user}/.motion/motion.conf (where {user] is your home directory).

Also create a folder to save captured video and images, such as: /home/{user}/motion

Change permissions for /home/{user}/.motion/motion.conf so you are able to read & write to this file, then open it with a text editor.

Change the following settings in this config file, removing any leading ";" characters to enable required options:-

```

Set target_dir /home/{user}/motion

netcam_url	{enter your camera url, see http://www.lavrsen.dk/foswiki/bin/view/Motion/ConfigOptionNetcamUrl}

webcam_port 8081

webcam_localhost off

control_port 8080

control_localhost off


```

To monitor video on a remote computer with Firefox, enter your host computer IP into Firefox address bar:-
{Host IP Address}:8081

...and you can remotely change motion.conf settings via Firefox with:-
{Host IP Address}:8080

I hope this helps.

---

