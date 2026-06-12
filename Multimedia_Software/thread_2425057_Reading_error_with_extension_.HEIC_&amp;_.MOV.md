---
title: "Reading error with extension .HEIC &amp; .MOV"
date: 2019-08-19
forum: Multimedia Software
---

### Post by azkov on 2019-08-19
Dear Ubuntu communties, 
First, let me introduce myself quickly. My name is Abel, I am completely new in Ubuntu environment. I am currently studying as Master's degree student in France (I am pretty sure you have already noticed that I was not a native speaker of Shakespear's tongue... :popcorn:) , I am interested into programming and widely all the tech environment (even if it is quite new for me). 

So, as a beginner_ I have some issues with the extension_ of my pictures and videos, especially **.HEIC & .MOV**  which were taken with an Iphone. (I found a topic which was explaining how to open such file with GIMP but it does not work on my computer...). 
[I]
I would like to know if someone have any solution relatively to this problem, isn't it ?)[/I]

Thank you for your time! 

Cheers, 

Azkov

---

### Post by DuckHook on 2019-08-19
Welcome to the forums, azkov.

A few things:

Linux does not use file extensions to launch apps. Instead, it relies on file metadata to determine the filetype. It then tries to launch the app associated with that MIME type.

.mov files are movie video files encoded using a proprietary codec. GIMP is a still graphics manipulation app and will not work on video files. For .mov files, you need to install the codec that will allow it to run in a standard Linux video app.

To install the required codec:```
sudo apt install ubuntu-restricted-extras
```

.heic files are a proprietary standard from MPEG that is primarily used by Apple devices. Because it is proprietary, Linux app makers have to reverse engineer the format in a clean room, then construct codecs to handle it. Only very recent versions of GIMP can handle these files (2.10.2 and newer). You don't say which version of Ubuntu you are using, but if it is Bionic, then that version of GIMP is only 2.8.22-1, which won't yet have the codec.

There are a number of strategies for dealing with heic files:

[LIST=1]
[*]Install the newest version of GIMP from the snap store.
[*]The version of GIMP in Ubuntu Dapper (19.04) should be able to work with heic files natively.
[*]Compile and run this open source [HEIF manipulation app]("http://nokiatech.github.io/heif/examples.html#download") from Nokia.
[*]Perhaps the "easiest" solution for newbies is to install libheif-examples from the repos, then convert the heic files into jpeg. However, you may wish to keep the heic files as heic, so this solution may not be optimal.
[/LIST]
If the last solution is okay:
```
sudo apt-get install libheif-examples
```…then follow instructions in man pages to convert file. Having never used the app, nor having any Apple devices, nor any heic files, I can't help you further in the use of the app.

---

### Post by azkov on 2019-09-08
> **DuckHook said:**
> Welcome to the forums, azkov.

A few things:

Linux does not use file extensions to launch apps. Instead, it relies on file metadata to determine the filetype. It then tries to launch the app associated with that MIME type.

.mov files are movie video files encoded using a proprietary codec. GIMP is a still graphics manipulation app and will not work on video files. For .mov files, you need to install the codec that will allow it to run in a standard Linux video app.

To install the required codec:```
sudo apt install ubuntu-restricted-extras
```

.heic files are a proprietary standard from MPEG that is primarily used by Apple devices. Because it is proprietary, Linux app makers have to reverse engineer the format in a clean room, then construct codecs to handle it. Only very recent versions of GIMP can handle these files (2.10.2 and newer). You don't say which version of Ubuntu you are using, but if it is Bionic, then that version of GIMP is only 2.8.22-1, which won't yet have the codec.

There are a number of strategies for dealing with heic files:

[LIST=1]
[*]Install the newest version of GIMP from the snap store. 
[*]The version of GIMP in Ubuntu Dapper (19.04) should be able to work with heic files natively. 
[*]Compile and run this open source [HEIF manipulation app]("http://nokiatech.github.io/heif/examples.html#download") from Nokia. 
[*]Perhaps the "easiest" solution for newbies is to install libheif-examples from the repos, then convert the heic files into jpeg. However, you may wish to keep the heic files as heic, so this solution may not be optimal. 
[/LIST]
If the last solution is okay:
```
sudo apt-get install libheif-examples
```…then follow instructions in man pages to convert file. Having never used the app, nor having any Apple devices, nor any heic files, I can't help you further in the use of the app.


Dear Duck Hook,

Thank you very much for your answer. I am sorry for the delay I had a lot to do. 

Have a good evening, 

Azkov

---

### Post by (kyT%0) on 2019-09-08
like already stated gimp is for images. for .mov mpv does a swell job.

to install via terminal : sudo apt install mpv

---

