---
title: "HOWTO: Cast/Stream local media on chromecast"
date: 2014-02-16
forum: Multimedia Software
---

### Post by abid_naqvi83 on 2014-02-16
With Google releasing the Chromecast SDK I finally ordered one and sat down to solve the primary desire for such a device: streaming local content from your computer (running Ubuntu) to the Chromecast to play it on your TV. Starting with this [sample project]("https://github.com/googlecast/CastHelloVideo-chrome") that Google kindly provided for developers I was able to create a python application that reads files from a specified folder and then creates a website (served by uwsgi and nginx) that can be used to select media and then cast/stream it to the Chromecast. I was able to get high quality content playing perfectly over the WiFi at approximately 650 kbps.

**Note:**

This solution does NOT require any hacking of the Chromecast, writing a new Chromecast application (it uses the default media receiver) or registering anything with the Google backend.

I have only been able to get mp3 and mp4 files to play. Specifically avi files do not play, probably because no browser supports avi in HTML5 video tags.

**Summary:**

In Ubuntu simply clone the project and use the Makefile to install and deploy the solution:

```
git clone git@github.com:abid-mujtaba/local-chromecast.git
cd local-chromecast
sudo make install
sudo make start
```

and then to open the website navigate to [http://localhost:3435](http://localhost:3435) or simply issue ***make run***.

**Details:**

I started with the sample Google project which had all the required functionality built in. It had a list of urls hard-coded in to the javascript which it could cast to the Chromecast. The Chromecast would then use the urls to display the media. The computer works only as a remote control of sorts in this situation. To cast local content I needed to set up a server from which the Chromecast could stream the media. Solution: nginx.

I decided that a sub-folder (/media) will contain all the media files one wants to cast (ideally symlinks to the media files). These are made available as static files via nginx. The Google sample code is a website. Since I needed to dynamically read the content of the media sub-folder and place it both in the website html and the javascript that does the actual business of sending media information to the Chromecast I chose python and uwsgi.

I modified the sample index.html to become a Jinja2 template and I wrote a simple python application script (intended to be served by uwsgi) to read the media sub-folder and use the Jinja2 template to place the media information in both the html and script sections. A socket is used to wrap nginx around the uwsgi and voila the pieces all come together.

Finally I wrote a makefile to automate the process of installing, configuring and deploying the servers (nginx and uwsgi) making it (pun intended) a relatively painless process to deploy.

---

### Post by frodolf on 2014-03-01
Interesting... But when I try to clone the project, github returns a "permission denied". Did you remove the files?

---

### Post by abid_naqvi83 on 2014-03-01
No the files are still there. The "permission denied" probably means you don't have an SSH key registered with github. You can use the https link instead:

```
git clone https://github.com/abid-mujtaba/local-chromecast.git
```

---

### Post by Lechasseur on 2014-03-25
Thanks for providing this solution. I installed the application as proposed but I receive the following error message:

pip install Jinja2
make: pip: Kommando nicht gefunden 
make: *** [install] Fehler 127

i.e. command not found
error 127

Any ideas? 

--> problem solved. Proper installation of pip helped.

----

Kubuntu 13.10
64 bit

---

### Post by dhbolthausen on 2014-12-07
Hello and "Thank You" for this little app. I have loaded it in Ubuntu 14.04 and it is working fine. I did have to load pip - but that was it and it then installed without a hitch. Remember readers that you have to link or put the media files in the directory that it tells you once you have it up in running. Great Job - hope there are improvements - like recursive folder reading. Thanks!

---

