---
title: "Autoupload spectacle screenshots"
date: 2017-05-05
forum: Multimedia Software
---

### Post by Alvin_Johansson on 2017-05-05
Hello everyone! 

I'm an avid ShareX user on Windows and really miss the upload functionality it uses. I've been looking around in the Spectacle settings and found that you probably could set it up to upload captured files to something like puush. the problem is that I'm really new to Kubuntu and don't really understand all that much. If anyone knows how to do this I greatly appreciate the help. 

Thanks for reading // Alvin

---

### Post by TheFu on 2017-05-05
Welcome to the forums.

Many of the terms you use are completely new to me.
Automation is the main thing that Unix/Linux systems do 1000x better than Windows, IMHO.  Almost anything can be automated with a tiny bit of effort. 

[https://stackoverflow.com/questions/17633586/how-to-upload-files-to-puush-from-web-server](https://stackoverflow.com/questions/17633586/how-to-upload-files-to-puush-from-web-server) seems to say that Puush uses a non-standard protocol. They make clients for other OSes, but not Linux.  
There are a few github projects like [https://github.com/sunmockyang/puush-linux](https://github.com/sunmockyang/puush-linux) which might be useful. It is a bash script with a few dependencies. 
I'd look at each of the projects before deciding on 1.

Basic bash scripting is a standard skill for Linux people. You don't need to be an expert. We all start by typing commands into a shell. Then we take those same commands and put them into a file and chmod +x on the file so it will run.  Eventually, we don't want to do exactly the same thing, but almost the same thing over and over.  Our scripts are modified and become slightly more flexible and usually a little more complex. All this happens over time. We have to crawl, stand, bobble, walk, jog, run, sprint, in that order. That is the nature of scripting.  I estimate this is a 'bobble-level' task.

Spectacle doesn't have uploading built-in.

---

### Post by vasa1 on 2017-05-05
What about [shutter]("http://shutter-project.org/")? It's in the repos.
> Shutter is a feature-rich screenshot program for Linux based operating systems such as Ubuntu. You can take a screenshot of a specific area, window, your whole screen, or even of a website &#8211; apply different effects to it, draw on it to highlight points, and then upload to an image hosting site, all within one window. But I doubt it will automatically upload the image. A few more clicks maybe needed!

---

