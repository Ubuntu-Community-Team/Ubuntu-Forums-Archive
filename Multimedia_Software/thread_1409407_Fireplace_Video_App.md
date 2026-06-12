---
title: "Fireplace Video App"
date: 2010-02-17
forum: Multimedia Software
---

### Post by SuperMike on 2010-02-17
I'm a freelance web developer who likes to look at a fireplace occasionally. Unfortunately I don't have one. It would be nice to have one on my desktop because I have a dual-screen monitor arrangement and one of these could display the app in a smallish window. Does anyone know how I might be able to get a video like this...

[http://www.youtube.com/watch?v=H6sE1GLsRaE&feature=related](http://www.youtube.com/watch?v=H6sE1GLsRaE&feature=related)

...in a nicely blended loop to display in a resizable window. Don't want controls for the video, just the video itself.

I suppose one avenue would be that I could make some kind of Mozilla Prism app that either displays an animated GIF of a fireplace, or plays a Flash video in a loop.

Mozilla Prism: [http://prism.mozilla.com/](http://prism.mozilla.com/)

---

### Post by HappyFeet on 2010-02-17
[Here]("http://thepiratebay.org/torrent/4555210/Yule_Log_Fire_in_HD_720p_for_PC_X-Box_360_portable_devices_-_Gre") is the torrent file for *Yule Log Fire in HD 720p for PC/X-Box 360/portable devices*.

---

### Post by SuperMike on 2010-02-17
I found yet another solution. This is really cool and can be used for all kinds of things, including as a wrapper to any website, including a stock ticker, Gmail, Facebook, Twitter, and many more sites.

All you need is Firefox, a GIF, and a single plugin. A sixth-grader could make this "app". This might be a neat thing for a teacher to share with students for fun. In fact, with slight alteration of the instructions, it can be done on Mac and Windows -- not just Linux.

1. This requires Firefox, but only temporarily. It may or may not require GNOME -- I'm not certain. GNOME is what I use. In my case I have Ubuntu 8.04 with the very latest Firefox installed on my PC rather than the one that came bundled with Ubuntu. If you have Google Chrome as your default browser, hey, that's fine -- you just need Firefox installed on your system and it will only be used for these small apps. You also don't need to make FF your default browser -- you can stick with whatever floats your boat.

2. Let's get started. Create a project folder on your computer called "fireplace". I put my custom apps in a "bin" folder in my home directory, so I stuck my folder there.

3. Find a fireplace animated GIF that you want and like by typing in ["fireplace animated gif" on Google Images]("http://spicegrillusa.com/FireplaceAnimatedFire.gif") and surfing a bit. Go to the site to see the image gif file, rightclick in Firefox, and choose Save to save the file in your fireplace project folder.

4. Now create the following HTML file called "fireplace.html" in your project folder, modifying as you need:

[HTML]<html>
<head><title>Fireplace</title>
<style type="text/css">
BODY,HTML {
margin:0;
padding:0;
background-color:#000;
width:100%;
height:100%;
}
</style>
</head>
<body>
<img src="images/fire1.gif" alt="" width="100%" height="100%">
</body>
</html>
[/HTML]

5. See that width/height thing on the IMG tag? That can be altered to either a static height, static width, static both height and width, or keep as is with 100% or some other percentage. I like the percentage because it lets me resize the window and the image resizes with it. Notice also that I created a subfolder "images" in my fireplace folder and that's where "fire1.gif" was put. In your case you can do this differently.

6. Now you need to install the Prism Plugin for Firefox. It's located here:

[http://prism.mozilla.com/started/](http://prism.mozilla.com/started/)

Choose the "Download Firefox Extension" version and then install it. It will make Firefox need to restart when finished.

7. Now open Firefox and do File, Open File, and go browsing for this fireplace.html file. Select it and you'll see it displays it immediately, but it's like super-massive and uncool. Ignore that for now.

8. Go to the menus (in my case it's under Tools) and choose "Convert Website to Application". When the window pops up, type in a titlename if you want it different than the default, check off Desktop to create a desktop icon, and then change the icon to any fireplace or fire icon you have on your computer or can find from the web. (In my case I just made a 64x64 PNG image of the animated gif, but then chose Flatten Image in Gimp, as well as cropped it a good bit.) Click OK and it will make the desktop launcher on your desktop.

9. Find the icon and doubleclick it. Kapoof! You now have a virtual fireplace you can take anywhere with you. Now resize the window to the size you prefer -- it will remember this size the next time you open it.

---

### Post by shardinio on 2011-01-27
Hi There

I dont know an app but I know where you can download a hd fireplace at [http://www.fireplacedownloads.com](http://www.fireplacedownloads.com) They have a good selection and saves you messing about.

---

### Post by shardinio on 2011-01-27
oh, and you can see one of the videos on youtube at [http://www.youtube.com/watch?v=POJlQy8nANo](http://www.youtube.com/watch?v=POJlQy8nANo)

hope you enjoy

---

