---
title: "Web Scripting - Help Needed"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by jstvincent on 2011-04-25
I am running Ubuntu Desktop 10.04 LTS and finally got Apache2 installed and working correctly, now I want to make some sort of page that I can run the webpage (on my network, Intranet-type) on another computer and control the screen output of the server itself, such as uploading a picture via the Website and loading it to be the desktop background. I want to eventually use this computer with a projector as the screen and project images from the projector by loading them through a web page.
 
For specifics, I need some code to work with (already written and how to implement) or where to go for examples of this type of code. I would like to avoid installing ASP.NET on my server, as it looks fairly complicated, so if possible, please avoid ASP.NET scripts to run this system. (I will use them, it may just take me a while to get them tested, when I get around to installing ASP.NET).
 
Also, is there any chance that ASP.NET comes with Ubuntu Desktop 10.04? If so, please point me on how to set it up with Apache2 and then feel free to help my screen control idea in ASP!
 
Thanks,
 
jstvincent
 
They say the sky is the limit; I say the shell is the limit.

---

### Post by SeijiSensei on 2011-04-25
ASP and .NET are Microsoft constructs.  Most people in the *nix world use things like PHP, Perl, Ruby, or Python to handle web scripting.

However if you just want to display a bunch of images, you can put them in a directory that Apache can share like /var/www/, then visit [http://localhost/](http://localhost/) using a browser on the machine where Apache is running.  If you assign the pictures numeric filenames, you can control their ordering.

This is hardly the easiest way to run a slide show, though.  Image gallery software like **Gwenview** include slide shows as a built-in feature.  That's going to be a lot easier to manage than trying to deal with Apache and its security restrictions on the default /var/www web directory.

With Gwenview, you'd just put the images in a folder like $HOME/Pictures, point Gwenview at the folder, pick Full Screen, then Start Slideshow.  You can control when the pictures change with the keyboard or mouse, and can use the drop-down menu at the top to go forward or back as needed.

---

### Post by skullmunky on 2011-04-25
I'm curious about what it is you're trying to do.  Computer A is running apache, and you want to connect to it remotely from Computer B through a web browser, and upload an image which Computer A will then use as its desktop background?  I guess it seems a little unusual because generally your web server is something you stick in a server rack or a closet, not something you run your regular desktop applications on.  

But perhaps your application is something like a slideshow which you can dynamically update from a remote location, like flatscreen monitor in a lobby or other public space which you want to display a daily sequence of images or something.

Here's one way:

1. find a standard PHP image uploading script.  put it in /var/www, configure it to upload images into a particular folder, like /var/www/images, or /home/joe/slideshow, etc.  there will be permission wackiness you will need to deal with when doing this, but it's not that bad.

2. I agree, gwenview is a great slideshow program.  If you want it to really be the desktop background, just go to the desktop settings, set the wallpaper mode to "slideshow" and set the folder to be the one you have the PHP script uploading pictures into.

Actually as I read your description a little more this sounds more and more like an art installation.  Perhaps you want the uploaded image to immediately appear on the projection?  In that case it is a little trickier and actually kind of an interesting problem.  The naive approach is just to display a webpage that constantly refreshes with the latest images.  But I think you want an RPC mechanism to push the latest image to your display program.

One of the python web programming frameworks probably has this built in nicely, but if you want to hack it together yourself I'd look at mod_python for apache, a few lines of code with PyGame to display the image, and something like the RPyC python remote procedure call library to glue them together.

---

