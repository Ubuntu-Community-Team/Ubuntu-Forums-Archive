---
title: "Remote Control pain."
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by hotani on 2007-04-29
I have an ATI Remote Wonder. It worked great in OSX, even had a spiffy control panel that would allow me to configure it differently for specific applications. Then I moved to Ubuntu.

It has been nothing but pain to try and get this thing to do what I need, which is a rather short list: 
1- navigate the menus in whatever media center app I'm using (trying Elisa at the moment)
2- Play/Pause/Stop/etc... when in a video player 

Here is the problem with navigating menus: Elisa requires a "Return" action to select something. When I set a key on the remote to Return, it takes over that key on the keyboard. So if i set it to '0', when I hit '0' I don't get the number, I get a Return action. Same goes for any key on the remote. For some reason it is perma-linked to keys on the keyboard and there is no 'RETURN' on the remote--the "ok" button conveniently does absolutely nothing.

Arrow keys are somewhat universal, and navigating menus usually works ok. In VLC, I can actually change the key commands in the app itself to match the remote that has been configured to match the media center. That only works with MythTV, which I despise using because of all the setup pains I have to go through for a bunch of crap I'm not even using (MySQL, backend server, config, config, config, config....). Elisa is nice because of its simplicity, but when I tried to configure the remote, it all went down in flames.

The pause button on the remote is tied to the keyboard pause which is tied to rhythmbox pause. Hitting 'pause' while watching a video causes the music to start up, and it won't pause the video. So i have to set it to some other weird key like "c". Then I have to remember that "c" is pause, "that weird button with the check on it" is play, I have no way to select a movie other than getting up and walking to the keyboard (yes, my computer is the tv, I have a 37" monitor).

So I'm about ready to take this awful piece of crap out on the front sidewalk and hit it with a hammer. Is there a remote that works better in linux? One with an actual control panel? One that is (omg!) logical to use and fairly painless to set up?

The biggest problem is that no two media players agree on control keys. Then if you do happen to get them all happy (because, as we all know, there is no 'one size fits all' media player for linux, we gotta have and use 4!), whatever magical configuration that is probably has issues with the media center controls!

Maybe I'll bail on the whole thing and get a media player stand-alone box (with its own remote!) that plays vids off my machine. Oh, wait, they're probably all "Windows-only."

---

### Post by isecore on 2008-04-30
I wish I had a solution for you, but I'm in the same place. Found an old ATI Remote Wonder in the shelves here, felt it was perfect to use to build a simple HTPC for myself. Figured I'd go with Ubuntu and Elisa as the combination (I have no interest in PVR-functionality) and tried setting up the remote.

Works fine, except that Elisa uses the backspace/return keys to navigate into and out of submenus. The remote doesn't send those keycodes! AAAARGH!

---

### Post by melaren on 2008-05-01
Hey guys, try this page: [https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

From the page: The Mythbuntu Team has developed a python script that will generate a sane remote control mapping to use or at least start from. It grabs all of the possible buttons and remotes from /etc/lirc/lircd.conf and maps them over for MythTV, Xine, MPlayer, VLC, Totem, & Elisa.

---

