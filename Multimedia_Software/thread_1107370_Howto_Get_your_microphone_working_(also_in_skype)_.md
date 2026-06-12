---
title: "Howto: Get your microphone working (also in skype) in 9.04 x64"
date: 2009-03-26
forum: Multimedia Software
---

### Post by markg85 on 2009-03-26
Hi,

A few days ago i [posted]("http://blog.mageprojects.com/2009/03/24/get-your-microphone-working-in-ubuntu-904-and-skype-x64/") a extensive howto on my [blog]("http://blog.mageprojects.com") that describes exactly what i did to get my microphone working on ubuntu 9.04 and get it working with skype (x64 version). I will post the plain version here. You will have to go to my blog to see the full version with images that describe it in more detail.

[http://blog.mageprojects.com/2009/03/24/get-your-microphone-working-in-ubuntu-904-and-skype-x64/](http://blog.mageprojects.com/2009/03/24/get-your-microphone-working-in-ubuntu-904-and-skype-x64/)

Plain version
> Hi,

After hours of testing i finally found out how to get my microphone to work under ubuntu.
The thing that i had already working “out of the box” is that you could talk in your microphone and you would hear it come out of your speakers but somehow it wasn’t recording it when i tried to record the input from the microphone. So once i got it working i started writing this howto so that others can get a microphone (and skype) working as well. This howto should work in any linux distribution since it’s not ubuntu specific. It is gnome specific so i don’t know how well this works (if at all) in kde.

The first thing i did (and you should do as well) is open a console (ALT+F2 -> gnome-terminal or xterm).
Now type this:

alsamixer

now you should see something like this: << screenshot on the blog post >>

My advise would be to just put all at max EXEPT for the values that contain anything like “boost”.. i put them up to test with and it didn’t really improve microphone quality or made it louder. It just made it sound horrible and it was even affecting the normal playback sound as well.

Now once this is done press TAB in that alse mixes stuff. You should now get the properties for “Capture” (seen at the top left corner in those few lines of text) devices:
<< screenshot on the blog post >>

I’m not sure if anything here helped getting it working but i turned all “boost” things off and the rest on. Feel free to tweak those settings a bit to see if they actually do something with the microphone.

Now, once you’ve done this, you “should” have your microphone setup currectly and it should just work. There are just a few more issues. When you start recording your microphone imput you most likely don’t hear anything when you play it back. That’s because the “Sound Capture” setting in gnome’s sound settings is set wrong.
So open the gnome sound settings: System -> Preferences -> Sound and you should see this:

<< screenshot on the blog post >>

The way to test if your microphone is actually working is by clicking on the “Test” button behind “Sound capture”. Press test and talk in your microphone. If you hear yourself with a slight delay from the speakers you have it working. If not try every option in the list (in the screenshot it’s on “ALSa - Advanced Linux Sound Architecture” between the “Sound capture:”  and “test”. one of them should be working. Also note that there seems to be double values with exactly the same name but they do act differently! atleast that was the case for me.

Once you’ve done that and you found one that seems to be working (the right one for me was: “HDA Intel something…” which was in the list twice. the top one did it for me) then you can start recording your microphone if you want. Try it out in gnome-sound-recorder but i won’t go deeper in that stuff.

Oke, by now your microphone should be working and you can record your microphone input and it seems to be working fine. If that’s the case then you now install skype (i used this link: [http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64) which should be the latest x64 version) Open skype and go to the “Sound Devices” tab in skype.
<< screenshot on the blog post >>

For me the Sound out and Ringing was just fine but the Sound in was wrong. To get that one good you have to (sadly) test every option in the Sound in list and “Make a test call”… say something and see if it gets out of your boxes after the second beep.

This is how i got it working.
Here are my settings from the volume control stuff in gnome incase you might be interested in those as well.

<< screenshot on the blog post >>

Note for the image above: i have no clue why the microphone icons have a cross in there. i could turn them off/on whatever i wanted but the setting didn’t seem to be saved and didn’t seem to mather for the microphone.

<< screenshot on the blog post >>

It should all be working fine now.

I hope this howto has been helpfull for you. If you found another solution or have something to add to this feel free to post so in the comments.
Good luck,
Mark

I hope this helps anyone that had the same issue as me: "*HOW do i get that microphone to work in ubuntu with pulseaudio.. and how do i get it working with skype?*"

---

