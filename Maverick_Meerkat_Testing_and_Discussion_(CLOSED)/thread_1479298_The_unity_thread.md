---
title: "The unity thread"
date: 2010-05-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-05-10
Seeing as I've seen one question about unity in the gnome-shell thread. I start this thread. for those wanting to try out Unity, the ppa is [here]("https://edge.launchpad.net/~canonical-dx-team/+archive/une"). I'm currently running it on my netbook.

---

### Post by Sashin on 2010-05-10
Anyone else getting some "BadWindow" error?

---

### Post by MacUntu on 2010-05-10
How can you start a second instance of a program? I tried right-click and middle-click like it works in Win 7 but that didn't work. Am I doing something wrong or is it yet too prototype? :D

Anyways, it looks promising! Too bad I'll never buy a netbook. :P

> **Sashin said:**
> Anyone else getting some "BadWindow" error?

Nope. I first started it within a GNOME session; worked but threw tons of warnings. Then I started a Unity session via GDM - .xsession-errors still was full of warnings but much less than when started from within a GNOME session.

---

### Post by cariboo on 2010-05-10
I just installed it an hour ago, it doesn't look like any of the key bindings work either. ALt-F2 doesn't bring a the run dialog.

It looks like it is only running a single desktop, and there no icons in the top panel for other running apps. I think this may be pre-pre-alpha :)

---

### Post by descendent87 on 2010-05-10
Tried it on my dell mini (GMA500, using psb driver that lucozade got working for lucid) and just gives me a black screen, cursor shows up but nothing else

---

### Post by cariboo on 2010-05-10
Another screenshot after a bit of playing

---

### Post by plun on 2010-05-10
Up and running.....:popcorn:

I must launch the unity launcher from a terminal.

Testing...

[[img]http://ubuntu-pics.de/thumb/60633/snapshot23_6ytxI1.png[/img]](http://ubuntu-pics.de/bild/60633/snapshot23_6ytxI1.png)

---

### Post by DannyBiker on 2010-05-10
Okay I need help here.
I installed the interface on my tablet pc but I get the "white screen" bug : everything is white. I can see some notifications appear properly (such as wifi connection) and the system seems to run fine except that I can't see a thing.
Problem is : I didn't activate the log-in screen so I'm stuck. When I boot my device, it loads the Unity session and I can't do anything. When I try to force a halt with the on/off button, it looks like the "turn off" menu appears (I can see its shape but no content), but no "Disconnect" option there (I always found that silly and this certainly confirms it).
I tried "alt+f2 : metacity --replace" but I don't see any window appearing.

Please, tell me there's something that can be done ! Using a live CD session perhaps ?

Thanks !

---

### Post by Sashin on 2010-05-10
Yep, I get that when logging in from login screen. However from terminal it says:

> The program 'unity' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 949 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


---

### Post by plun on 2010-05-10
sabdlf about unity

[http://www.markshuttleworth.com/archives/383](http://www.markshuttleworth.com/archives/383)

;-)

---

### Post by LKjell on 2010-05-10
It does look like the netbook remix thing. Wouldn't be better to just focus on one thing?

---

### Post by cariboo on 2010-05-10
It is specifically for netbooks, check out the link in plun's post.

---

### Post by Atermoon on 2010-05-10
I get a white screen and nothing else. Works fine on my Lucid install though.

---

### Post by cariboo on 2010-05-10
I'm running it on my Compaq Mini 110 with i945 graphics chips set, I've been playing with it most of the day with zero problems. The netbook is running Lucid UNE.

---

### Post by Rasa1111 on 2010-05-10
you can make the desktop do basically the same thing without any special app.

could even make it have the exact same background, 
mine is just not expanded, and ive got the width a bit smaller. 
2nd pic a bit wider.

but for people on desktops, who cant run a dock for some reason, 
this works decent, and you can make it look anyway you want, anywhere you want, background, size, and all, even make it hide itself. lol

[mostly for the n00bs], i dont mean to tell you pros stuff you already know. lol

---

### Post by tjeremiah on 2010-05-10
does anyone know how to remove the second clock in the indicator applet when returning to GNOME ?

---

### Post by godhika on 2010-05-11
> **tjeremiah said:**
> does anyone know how to remove the second clock in the indicator applet when returning to GNOME ?

Ahm....right click on it -----> remove from panel.

---

### Post by zoomy942 on 2010-05-11
i might install it tomorrow.

---

### Post by jppr on 2010-05-11
> **Rasa1111 said:**
> you can make the desktop do basically the same thing without any special app.

could even make it have the exact same background, 
mine is just not expanded, and ive got the width a bit smaller. 
2nd pic a bit wider.

but for people on desktops, who cant run a dock for some reason, 
this works decent, and you can make it look anyway you want, anywhere you want, background, size, and all, even make it hide itself. lol

[mostly for the n00bs], i dont mean to tell you pros stuff you already know. lol

I install it my desktop, system start but I don´t have panels. When I start Gnome it freeze and I must start system  -/.xsession

---

### Post by Rasa1111 on 2010-05-11
> **jppr said:**
> I install it my desktop, system start but I don´t have panels. When I start Gnome it freeze and I must start system  -/.xsession

hmm..

 do you mean 'compiz'?
that makes mine freeze to..
but this doesnt need anything special.. 

 you can add another panel easily..
no special/visual effects needed.

Just right click on the top or bottom panels..
and click "new panel" , then it will put the panel up, and go wherever you choose. 
 then~ you can right click the new panel, 
and hit "properties"..
then from there, change how it looks, 
it's size, it's color/background/transparency, position, 
auto-hide or not, add hide buttons to it, expand it,  etc.

 if you can use your desktop, you can do this.

 then you can drag icons for apps into it, or add anything else you want in it. by right clicking, and hitting "add to panel"

apologies if im telling you something you already know and i am simply confused. . lol :)

---

### Post by valorin on 2010-05-11
> **tjeremiah said:**
> does anyone know how to remove the second clock in the indicator applet when returning to GNOME ?

> **godhika said:**
> Ahm....right click on it -----> remove from panel.

That either removes the original (big with calendar on the click) clock, or the entire Indicator Applet...

I've got the same problem with the little one being there :s

I am also getting the white screen when I try and run Unity... I guess I should just stuck with normal Gnome.

:(

---

### Post by godhika on 2010-05-11
> **valorin said:**
> That either removes the original (big with calendar on the click) clock, or the entire Indicator Applet...

I've got the same problem with the little one being there :s

I am also getting the white screen when I try and run Unity... I guess I should just stuck with normal Gnome.

:(

Oh sorry you are right. I removed the old one and was under the impression the new indicator is also seperate. My fault

---

### Post by MacUntu on 2010-05-11
Just uninstall indicator-datetime.

---

### Post by Eclipse. on 2010-05-11
I have the white screen bug. Anybody got any ideas?

---

### Post by John_Swing on 2010-05-11
> **MacUntu said:**
> Just uninstall indicator-daytime.

I tried to remove indicator-daytime but apt-get don't find it...

---

### Post by valorin on 2010-05-11
> **MacUntu said:**
> Just uninstall indicator-daytime.

> **John_Swing said:**
> I tried to remove indicator-daytime but apt-get don't find it...

The package is 'indicator-datetime' not indicator-daytime' :guitar:

Thanks MacUntu :)

---

### Post by rayraven on 2010-05-11
> **Eclipse. said:**
> I have the white screen bug. Anybody got any ideas?

Same here, although running it from the terminal works.
Seems very pre-alpha though, and i dont like the fact that the icons are hardcoded? it uses the default ubuntu icons even though i am using elementary icons.

Would be nice to be able to move the dock too ;)

---

### Post by MacUntu on 2010-05-11
LOL sorry, that's what happens when I post before I had my first coffee. :D

---

### Post by Eclipse. on 2010-05-11
> **rayraven said:**
> Same here, although running it from the terminal works.
Seems very pre-alpha though, and i dont like the fact that the icons are hardcoded? it uses the default ubuntu icons even though i am using elementary icons.

Would be nice to be able to move the dock too ;)

You wouldnt have gnome-shell ppa by any chance? I think its something screwing up with mutter from that.

---

### Post by zekopeko on 2010-05-11
> **cariboo907 said:**
> I just installed it an hour ago, it doesn't look like any of the key bindings work either. ALt-F2 doesn't bring a the run dialog.

It looks like it is only running a single desktop, and there no icons in the top panel for other running apps. I think this may be pre-pre-alpha :)

Thats because the top panel isn't gnome-panel. It's a custom panel made in Clutter.

---

### Post by valorin on 2010-05-11
> **Eclipse. said:**
> You wouldnt have gnome-shell ppa by any chance? I think its something screwing up with mutter from that.

Yes, I am running a gnome-shell PPA (ricotz PPA).

I'll try and uninstall gnome-shell and remove the PPA, and see what happens.

---

### Post by Eclipse. on 2010-05-11
> **valorin said:**
> Yes, I am running a gnome-shell PPA (ricotz PPA).

I'll try and uninstall gnome-shell and remove the PPA, and see what happens.

I think thats our problem. :) I will report back soon.

---

### Post by valorin on 2010-05-11
/me does a happy dance!

Following these steps I am now running in Unity:

```
1. Disabled my PPA for gnome-shell via 'Software Sources'
2. sudo apt-get remove gnome-shell unity mutter
3. sudo apt-get install unity
```

Basically I had to force it to use the version of mutter from the Unity PPA rather than from the gnome-shell PPA.

---

### Post by rayraven on 2010-05-11
> **Eclipse. said:**
> You wouldnt have gnome-shell ppa by any chance? I think its something screwing up with mutter from that.

Yes, i am.
And now i am having tough time deciding whether to keep gnome shell or unity :)

---

### Post by tjeremiah on 2010-05-11
> **godhika said:**
> Ahm....right click on it -----> remove from panel.
EDIT: Never mind. Someone already replied saying that this removes the entire app. and not just the clock..

---

### Post by rubenverweij on 2010-05-11
This looks amazing! Certainly as good as, and in my opinion, better than GNOME Shell!
I really like the icons on the left with the triangles next to them to indicate the program is running/focused.
I only hope they add the option to change the background :) and make it easier to get to apps that are not in the launcher. But concerning this is kind of a preview, I'm sure that'll be worked out.
I really like it! :P

---

### Post by cariboo on 2010-05-11
The ability is already there, just go to Appearances in the Application window, to set it. That was one of the first things I did. :)

---

### Post by godhika on 2010-05-11
I think he is talking about the panel background.But that is (somehow) also possible: Just change the background pictures in the usr/share/unity/themes folder.

---

### Post by cariboo on 2010-05-11
I think the button background is hard coded, but buttons scroll up and down, so if you have enough buttons you never see the background. :)

Another thing I just found out is that are only four panels allowed if you click the Ubuntu logo in the top left corner, any mor, and only one panel shows.

---

### Post by frustphil on 2010-05-11
> **cariboo907 said:**
> The ability is already there, just go to Appearances in the Application window, to set it. That was one of the first things I did. :)

Wow. Definitely wow! :-)

Question: Nothing has been defined for the desktop right?

---

### Post by ElSlunko on 2010-05-11
Looks great!

---

### Post by rubenverweij on 2010-05-12
> **cariboo907 said:**
> The ability is already there, just go to Appearances in the Application window, to set it. That was one of the first things I did. :)

Whoops... must have missed that. Thanks!

---

### Post by toor58 on 2010-05-13
Just installed Unity on my Asus eee pc 1005HAB. I am seeing some strange mess with the wallpapers. i have two screenshots. The first is a stock Ubuntu background. These wallpapers are all to large to fit properly. You can see only a small portion. Some other wallpapers also act like this.

The second screenshot shows a bing wallpaper. It appears to have two sizes of the same wallpaper. It looks like a compositing error of some sort, but I just do not know what.

Any ideas?

Next question. Is this where we will post on Unity, or are we going to get a seperate place?

Finally, does anyone know where we should post bugs, suggestion, etc, for Unity?

Thanks.

[IMG]http://farm5.static.flickr.com/4010/4604756438_82f124eef9.jpg[/IMG]


[IMG]http://farm2.static.flickr.com/1248/4604757384_2644e0328e.jpg[/IMG]

---

### Post by cariboo on 2010-05-13
I had to resize the wallpaper I use, to make it work. 

There is no official bug reporting system in place yet. To report bugs, contact the desktop experience team [here]("https://launchpad.net/~canonical-dx-team").

I would assume that once Unity makes its way into the regular repositories, the regular bug reporting channels will be valid.

Unity was only released for general use on this past Monday, so it may take a bit of time to get the rest of the infrastructure setup.

---

### Post by 23meg on 2010-05-13
You can report bugs in Unity's (upstream) bug tracker at Launchpad:

[https://bugs.launchpad.net/unity](https://bugs.launchpad.net/unity)

---

### Post by cariboo on 2010-05-13
thanks 23meg, I wasn't aware of that.

---

### Post by toor58 on 2010-05-13
Thanks guy's. I am really interested in this project, as i use my eee pc for nearly every thing. I am excited about the direction UNE is going. Looking forward to working with everyone on this.

---

### Post by la3875 on 2010-05-14
I couldnt help myself and installed and gave it a go. Like what I see, when I can see it! Whenever my cursor rolls over the sidebar screen flashes white. Also cant figure out how to get back to UNE as icon in top left seems inoperable.

Ideas?

---

### Post by zoomy942 on 2010-05-14
i was wondering the same thing.  i want to install it but how do i change from one to the other

---

### Post by go7Ul1ai on 2010-05-14
> **zoomy942 said:**
> i was wondering the same thing.  i want to install it but how do i change from one to the other

Once installed, log out and make sure the "Ubuntu Unity Netbook Edition" is selected under Sessions then log in. Once you want to go back to the default set up, log back out and select "GNOME" under Sessions :)

---

### Post by zoomy942 on 2010-05-14
> **lee.jarratt said:**
> Once installed, log out and make sure the "Ubuntu Unity Netbook Edition" is selected under Sessions then log in. Once you want to go back to the default set up, log back out and select "GNOME" under Sessions :)

ah.  so unity, the UNE and gnome all show up in the session menu at log in?

---

### Post by go7Ul1ai on 2010-05-14
> **zoomy942 said:**
> ah.  so unity, the UNE and gnome all show up in the session menu at log in?

Aye, but Unity and UNE are as one in this case

---

### Post by la3875 on 2010-05-14
True but i couldn't see an option as I am the only one using the computer i have it set to automatically log me in on start up.

What I did do however was login in recovery mode and use low graphics mode. In my case it actually ran unity with no resolution effects and I was able to go to applications and change my login session back to UNE. Now that I know I can recover I will play with it some more. Looks very promising! Would love to see it on my N810 ;-)

IMO Lucid is the best Ubuntu yet!

---

### Post by zoomy942 on 2010-05-14
> **lee.jarratt said:**
> Aye, but Unity and UNE are as one in this case



so i wont see both as separate entries?

---

### Post by go7Ul1ai on 2010-05-14
> **zoomy942 said:**
> so i wont see both as separate entries?

That's right.

---

### Post by zoomy942 on 2010-05-14
> **lee.jarratt said:**
> That's right.

oh.  looks like i wont be installing it then :)  i want to be able to switch between the two

---

### Post by cariboo on 2010-05-14
On my netbook I have the following choices at the login screen

[list]
[*] Failsafe Gnome
[*] GNOME
[*] Ubuntu Netbook Edition
[*] Ubuntu Netbook Edition 2D
[*] Ubuntu Unity Netbook Edition
[*] ~/.xseesion
[*] xterm
[/list]

---

### Post by go7Ul1ai on 2010-05-14
Oopsy, I may have misunderstood the question. Sorry!

---

### Post by zoomy942 on 2010-05-14
Alright.  i installed it and wow.  its something else.

i have noticed that dragging apps to the bar on the left doesnt make them stay there, and sometimes they dont even show up on it.

---

### Post by cariboo on 2010-05-14
What I've been doing, so far is going to the applications folder and just right clicking the app I want to add to the menu (dock?, dash?). 

Unity is nowhere near being complete, as there is a lot of functionality that we use every day missing. I created a bug for ALt-F2 not working, it has been put on the wish list.

---

### Post by meeples on 2010-05-15
been using it since it came out on my AAO, no problems except that of alt + f2, 

the interface is very nice, with the netbook remix i used it for a few days because it was pretty and switch backed to standard gnome, but when i used Unity and tried to use standard desktop today, it felt wrong. 

would love to try this out on a touch screen.

---

### Post by rubenverweij on 2010-05-15
> **zoomy942 said:**
> i have noticed that dragging apps to the bar on the left doesnt make them stay there, and sometimes they dont even show up on it.

I don't think there is any drag support yet, you can only bookmark (?) apps by launching them and then right clicking on their icon. There you'll see an option to add them.

---

### Post by shafin on 2010-05-15
Could any of you got unity to play nice with Virtualbox?

---

### Post by cariboo on 2010-05-15
> **rubenverweij said:**
> I don't think there is any drag support yet, you can only bookmark (?) apps by launching them and then right clicking on their icon. There you'll see an option to add them.

You can so far only add 10 items to the launcher, I added it to the bug list. bug [lpbug]#580707[/lpbug]

---

### Post by gnomeuser on 2010-05-16
I switched my netbook to using Unity, it is frightfully early and to be honest I am not sold on the parts were the layout differs from LightSource. 

The dock isn't really useful but I have to admit despite the early stage I already like it a whole lot more than gnome-shell for my netbook.

---

### Post by N2G(bn#7+ on 2010-05-16
Hi, wondering if anyone can provide some help here - I've installed Unity using
```
sudo apt-add-repository ppa:canonical-dx-team/une
sudo apt-get update
sudo apt-get install unity
```
and now want to run it but it's **not showing up in my GDM session menu**. Have done a google scour & can't see any evidence of someone else encountering this problem. Just wanted to test the waters - see if anyone has a solution or if I'm doing something silly - before I file a bug.

Thanks.

---

### Post by dsfitzpat on 2010-05-19
I decided to give unity a try and it seems to have potential, but I ended up going back to the standard netbook session for ease of use.  I'm a bit clumsy with the touchpad and accidentally dragged a couple of launchers off of the left-hand panel, which causes them to vanish.  Does anyone know a quick way to get them back without having to dig through the applications folder?
Also it would be nice if maximus worked the same as with the netbook edition - with the window title and close button up in the top panel (there's room for it) since vertical space is limited on a netbook.
A mildly annoying side effect when going back to the netbook edition desktop is that the installation of indicator-datetime leaves one with two clocks - and since the panel is unfortunately locked out in lucid, there's no way of getting rid of the second clock without uninstalling!

---

### Post by zekopeko on 2010-05-19
> **dsfitzpat said:**
> I decided to give unity a try and it seems to have potential, but I ended up going back to the standard netbook session for ease of use.  I'm a bit clumsy with the touchpad and accidentally dragged a couple of launchers off of the left-hand panel, which causes them to vanish.  Does anyone know a quick way to get them back without having to dig through the applications folder?
Also it would be nice if maximus worked the same as with the netbook edition - with the window title and close button up in the top panel (there's room for it) since vertical space is limited on a netbook.
A mildly annoying side effect when going back to the netbook edition desktop is that the installation of indicator-datetime leaves one with two clocks - and since the panel is unfortunately locked out in lucid, there's no way of getting rid of the second clock without uninstalling!

Every problem you encountered is going to be fixed by the time 10.10 comes out. Adding launchers is going be done with the yet-to-be-developed Dash overlay for accessing files and applications.

The maximus behavior is going to be integrated with the global menu that is going to appear in UNE 10.10.

To remove the indicator clock simply uninstall the indicator-datetime package from synaptic. That is currently the only way to have it gone.

I suggest you open a bug report on the accidental-dragging-of-launcher problem. This could be fixed by having some sort of lock for the dock.

---

### Post by wayneericgouin on 2010-05-22
If by chance you are seeing a white screen upon logging into the Unity session, I suggest you check if Mutter is already installed in Synaptic, as this will cause a conflict in the version of Mutter that Unity uses I.E.Gnome-Shell.

---

### Post by nanog on 2010-05-22
> yet-to-be-developed Dash overlay

The branches in the ppa don't seem to be updated very often. Is there a bazaar trunk where we can track development more closely?

---

### Post by zekopeko on 2010-05-22
> **nanog said:**
> The branches in the ppa don't seem to be updated very often. Is there a bazaar trunk where we can track development more closely?

[www.launchpad.net/unity](www.launchpad.net/unity)

But they haven't pushed anything new since the initial release. I'm thinking they are implementing this internally and will merge it when it's ready.

---

### Post by RobinC@Amethyst on 2010-05-27
> **shafin said:**
> Could any of you got unity to play nice with Virtualbox?

It works for me in the current Sun VBox 3.1.8-whatever; enough for me to run comparative review against Netbook Edition launcher: 
[http://catlingmindswipe.blogspot.com/2010/05/review-ubuntu-netbook-launcher-versus.html]("http://catlingmindswipe.blogspot.com/2010/05/review-ubuntu-netbook-launcher-versus.html").

Remember running with Compiz is a scant-maybe and Gnome-Shell Mutter a definite no-no.  **RC**

---

### Post by cariboo on 2010-05-27
> **nanog said:**
> The branches in the ppa don't seem to be updated very often. Is there a bazaar trunk where we can track development more closely?

From the Launchpad page it looks like there will be a milestone release on May 3, and a second milestone release on May 10th.

---

### Post by Merk42 on 2010-05-27
> **cariboo907 said:**
> From the Launchpad page it looks like there will be a milestone release on May 3, and a second milestone release on May 10th.

I hope you mean June...

---

### Post by ktp on 2010-05-27
> **Merk42 said:**
> I hope you mean June...

yep...seems to be June.

milestone 0.2.0 (2010-06-03)   
milestone 0.2.2 (2010-06-10)

---

### Post by ranch hand on 2010-05-27
> **Merk42 said:**
> I hope you mean June...
Me too. Other wise I am and my computer is way off.

---

### Post by cariboo on 2010-05-27
I did mean June. :)

---

### Post by wayneericgouin on 2010-05-28
Has anyone noticed the delay when closing running programs? I'm just wondering if it's me or if it's how it responds in it's current state.

---

### Post by frustphil on 2010-05-29
Anyone know how to disable auto-maximizing of windows upon launching? I am using Unity on my desktop and it's kind of weird when everything is maximized. 

I really love the shell or whatever you call it. It feels organized and clean compared to panel + docky/etc.

---

### Post by Eclipse. on 2010-05-29
> **frustphil said:**
> Anyone know how to disable auto-maximizing of windows upon launching? I am using Unity on my desktop and it's kind of weird when everything is maximized. 

I really love the shell or whatever you call it. It feels organized and clean compared to panel + docky/etc.

It presumes your on a netbook and must be launching maximus, "killall maximus" should do the trick.

Ooo firefox theme?

---

### Post by frustphil on 2010-05-29
> **Eclipse. said:**
> It presumes your on a netbook and must be launching maximus, "killall maximus" should do the trick.


I see. It says "No process found"?

> **Eclipse. said:**
> 
Ooo firefox theme?


Your asking the theme I am using? It's Dust...

I would like to add, this thing boots really fast and loads the shell almost instantly. :-)

---

### Post by ivotron on 2010-05-29
I wanted to test it on my laptop, but when the Unity session starts the panel starts to flash on and off and I'm unable to do anything. Have you experienced this issue?

---

### Post by cariboo on 2010-05-29
@ivotron, I believe bug #[lpbug]578585[/lpbug] is what you are suffering from.

---

### Post by ivotron on 2010-05-29
> **cariboo907 said:**
> @ivotron, I believe bug #[lpbug]578585[/lpbug] is what you are suffering from.

Indeed, thanks a lot.

---

### Post by Merk42 on 2010-06-08
I thought there was supposed to be some update for Alpha 1.  So I did a fresh install of Alpha 1 netbook, and added the ppa, but the package unity isn't even found.

---

### Post by cariboo on 2010-06-08
The packages are supposed to be added to the Maverick repos, June 10/11.

---

### Post by zekopeko on 2010-06-08
Does anybody else think that the Ubuntu circle in the upper left should have some hint its click-able? Something like a subtle glow.

---

### Post by nilarimogard on 2010-06-09
Unity is now in Maverick's repositories...

---

### Post by cariboo on 2010-06-10
Is anyone else seeing a huge rhythmbox icon in the applications folder?

---

### Post by Merk42 on 2010-06-10
> **cariboo907 said:**
> Is anyone else seeing a huge rhythmbox icon in the applications folder?

Yes, I am as well.

---

### Post by castrojo on 2010-06-11
You can file bugs here: [https://bugs.edge.launchpad.net/unity](https://bugs.edge.launchpad.net/unity)

Only 21(!) bugs so far? Surely we can break more than that!

EDIT: I am pretty sure the rhythmbox icon bug isn't unity related though

---

### Post by zekopeko on 2010-06-11
> **whiprush said:**
> You can file bugs here: [https://bugs.edge.launchpad.net/unity](https://bugs.edge.launchpad.net/unity)

Only 21(!) bugs so far? Surely we can break more than that!

EDIT: I am pretty sure the rhythmbox icon bug isn't unity related though

Are feature suggestions/UI enhancement welcome?

---

### Post by LiquidMeson on 2010-06-11
Not exactly related to the panel, but would be neat if everything in a corner was hot with a 500ms delay. Just throwing in out there...

---

### Post by castrojo on 2010-06-11
> **zekopeko said:**
> Are feature suggestions/UI enhancement welcome?

For larger ideas and topics the ayatana mailing list is probably a better place to discuss such things. However for little/obvious things then pile them on! (I just filed one myself)

---

### Post by castrojo on 2010-06-11
Ok Ken just pushed up a new appmenu-gtk. When you log in now and launch an app (like gedit), you should see the global menu in the top bar? Can someone confirm if they see that? (The menus themselves are still a bit buggy still)

---

### Post by MacUntu on 2010-06-11
I installed unity from the Maverick repos - should this add a unity session (didn't for me)? When starting it from within a GNOME session the gnome-panels stay.

---

### Post by cariboo on 2010-06-11
You should be able to select the session from the login screen, on my netbook it's called *Ubuntu Netbook Edition* previous versions had a separate *Unity* entry.

---

### Post by MacUntu on 2010-06-11
Thanks! Guess it's the good old "purge everything and reinstall" game then. :D

**Edit:**
Ok, installing unity alone didn't give me an entry but after installing - surprise - ubuntu-netbook it's there. :)

---

### Post by cariboo on 2010-06-11
> **whiprush said:**
> Ok Ken just pushed up a new appmenu-gtk. When you log in now and launch an app (like gedit), you should see the global menu in the top bar? Can someone confirm if they see that? (The menus themselves are still a bit buggy still)

The global menu works for gedit and gnome-terminal, although they both still have their own menu bar.

**Update:** VLC works too, but the menu is messed up see bug #[lpbug]592850[/lpbug]

---

### Post by castrojo on 2010-06-11
> **cariboo907 said:**
> The global menu works for gedit and gnome-terminal, although they both still have their own menu bar.

Yeah that's on purpose: we keep the old menu around so you can compare them both and see which items are out of order or don't work.

---

### Post by cariboo on 2010-06-11
Thanks.

---

### Post by ranch hand on 2010-06-11
I think I need some instruction here.   I have no idea what I have done wrong but there is evidence that I must have something or failed to do something.

I installed unity, unity-asset-pool and unity-dbg on one of my throw away installs.  Just ran upgrades and went to check on them to see if I want to upgrade my other installs.

Booted to gnome and every thing is fine.

Logged out and checked the options.  New entry!  dwm is what was there that was different so I picked it and logged in.  This seemed to go fine.

I sure hope that it didn't and from reading this thread I am sure that it didn't.  All I got was my usual background and an interesting narrow bar across the top of the screen.

The left end had the numbers 1 through 9 then a set of square brackets and an equals sign.  The only live thing was the brackets and they changed to a > connected to a diamond shape.  Click on that and it changed back.  Fun but not to useful.

The right end had dwm-x.x.x (should have written the numbers down).

The mouse pointer moved around the screen fine.  No left click or right click stuff that I could find anywhere.

Used tty2 to reboot and come back here.

This is on my only box, the desktop described below.

Now you can pile on and laugh at what ever obvious thing I failed to do.

---

### Post by zekopeko on 2010-06-11
dwm is a tiling window manager IIRC. You messed something. On Maverick it should say Ubuntu Netbook Edition and on Lucid Ubuntu Unity Netbook Edition or something similar.

---

### Post by ranch hand on 2010-06-11
Well, maybe I'll see what happens on another install.

I may have something else conflicting on there somehow.  When A2 comes out I'll use those partitions to try the ISO out on.   That ought to clean that up.

---

### Post by Merk42 on 2010-06-11
Doesn't seem to work in Virtualbox, even with Virtualbox Additions.  All I see is my desktop background.  No bar on the top or side, not even a mouse cursor.

---

### Post by cariboo on 2010-06-11
I haven't installed Global menu on my Lucid partition yet. but on Maverick there are only a few apps that work. Kde/Qt apps like vlc look really strange, you get _Media P_layback and _Audio instead of _M_edia P_l_ayback and _A_udio.

---

### Post by ranch hand on 2010-06-11
I installed the bugger on an other install of 10.10.  I am over on it now.

There is no option to boot to it on the login page.

It is installed, all three packages are installed.  I reinstalled them through synaptic.  Going to reboot and see what happens.

---

### Post by ranch hand on 2010-06-12
Nope, not a thing.

Had a problem using the system under gnome that I did not have before.  Synaptic freezes the system if started from the launcher.  Mouse pointer works but that is all. tty2 to get out.

This was not a problem when I was here earlier and the only difference is the installation of unity that I can see but I have no idea if it is really related.

Beats me just doesn,t seem to work at all.  I still think I must be doing some thing wrong.

---

### Post by MacUntu on 2010-06-12
To which process would I attach gdb to debug a crashing unity? Mutter?

---

### Post by elranchero on 2010-06-12
I'm having the same problem with my MSI Wind U100.
I installed the unity settings using the terminal commands at [ubuntugeek.com]("http://www.ubuntugeek.com/new-unity-release-ready-for-testing-in-ubuntu-10-1010-04.html#more-6211")

when the login window appears, the GUI shows my desktop background, then the screen goes white, then desktop background, then white screen,
repeat forever...

I can get to the screen that allows me to change to a different X windows session, and I can change that option. Sorry, don't know all the exact terminology here...
I can try to make it start something other than Unity, but even when I do - I still get that flashing white screen.

my system is totally hosed for now.

---

### Post by cariboo on 2010-06-13
@elranchero, it looks like you are suffering from bug #[lpbug]578585[/lpbug].

---

### Post by KdotJ on 2010-06-13
> **Merk42 said:**
> Doesn't seem to work in Virtualbox, even with Virtualbox Additions.  All I see is my desktop background.  No bar on the top or side, not even a mouse cursor.

I get the same thing in virtualbox too

---

### Post by clyderino on 2010-06-13
The unity interface for Meerkat is obviously in the early phases of development. Is there a Wiki or manual to tell us how to do various tasks (put a new application icon on the menu bar, for example) as it now stands?

---

### Post by ranch hand on 2010-06-13
In the upper right of the screen there is a search tool.

Using it would have turned up;

[http://ubuntuforums.org/showthread.php?t=1479298](http://ubuntuforums.org/showthread.php?t=1479298)

which currently listed directly below your post on the index page.  Let's not get too many threads on one subject.

---

### Post by castrojo on 2010-06-13
> The unity interface for Meerkat is obviously in the early phases of development. Is there a Wiki or manual to tell us how to do various tasks (put a new application icon on the menu bar, for example) as it now stands?

[https://wiki.ubuntu.com/DesktopTeam/Unity](https://wiki.ubuntu.com/DesktopTeam/Unity)

Feel free to add tips and stuff to that page!

---

### Post by cariboo on 2010-06-13
Merged unity threads.

---

### Post by ranch hand on 2010-06-13
OK, I'm back with my silly problem.

I have installed every thing I can find having to do with UNE an Unity on both my throw away installs of 10.10.  I do have an option to boot to it now.

What I get is the exact same desktop as logging into a gnome session.  This is not very interesting when you want to see something else.

So here is the question(s), if I install UNE on my desktop box will it
A>explode?
B>run right?
C>work full screen on my 1440x900 screen?

---

### Post by scradock on 2010-06-13
Filled with enthusiasm to join the FUN I misguidedly installed ubuntu-netbook and all its dependencies; checked that gdm would default to a Unity session, and re-booted. 

What I get is my desktop, plus my one start-up application (aMSN), but no panels, and nothing else. No launcher, no side-bars, nothing to access anything else.

Rats! Lost the gnome-panels - let's try removing all this new stuff. Tried that (Ctl-Alt-F1 to get a console, login and use apt-get remove on everything that I had just installed). That will surely re-set my session to gnome, with the panels and everything as before.

Nope.Same desktop, no panels, no menus.

I have tried right-clicking - no context menu. Alt+P gives a list of Plugins (in what?), but no other Alt+? seems to be effective. No other workspaces available, still no way to reset gdm to a gnome session....

Any ideas,anyone?

LATER: OK, fixed it - tried editing /etc/gdm/custom.conf from another install. It appears that installing Unity set "default session" to "une", but uninstalling it doesn't revert the change, or set to any sensible alternative.

---

### Post by cariboo on 2010-06-13
I used the instructions on page whiprush linked to. The first time I tried I got the white screen and nothing else, I then uninstalled gnome-shell, which also removed it's version of mutter. I then Logged out and seletected the Ubuntu Netbook session, logged back in again, and curses, :) everything worked as it should, that just isn't any fun. I also install appmenu-gtk and that worked too.

---

### Post by EveKnight75 on 2010-06-13
I'm just chiming in to say "me too".

As in: Unity doesn't work in VirtualBox even with 128 MB video memory and 3D acceleration enabled.

It manages to get to the desktop background and that's about it. No top panel or launcher panel or *Run* dialog (Alt+F2) or terminal (Ctrl+Alt+T).

At least I get a cursor which I can move around. Too bad it doesn't do me any good because there's nothing to click on.

I can still launch the Ubuntu Netbook 2D edition which brings up the old UNE interface. Does anyone think that this whole issue could be related to Mutter? I mean, the general advice is **not** to run Gnome-Shell in a virtual machine because of the lack of Mutter/Clutter support so the same thing could possibly apply to this situation.

---

### Post by cariboo on 2010-06-14
@EveKnight75, please use the default font color, the color you chose is hard for some of our members to see. We have members of all ages, from 8 - 80 please format your posts so everyone can read them.

---

### Post by EveKnight75 on 2010-06-14
I've already sent you a PM to clarify the matter and settle on a resolution. I'll go search out my other posts on the forums now.

I didn't realize that the font color could cause issues. If it's inconvenienced anyone, I apologize.

[COLOR=DarkGreen]EveKnight75[/COLOR]

---

### Post by MacUntu on 2010-06-14
Please confirm:

"Unable to set a solid color as background"
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/594232](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/594232)
-> should be easy to reproduce

"Window overview: odd representation of (partially) off-screen windows"
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/594221](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/594221)
-> ditto

"SIGSEGV in _clutter_stage_has_full_redraw_queued"
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/594209](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/594209)
-> this one's more difficult to reproduce as it just randomly happens when zooming out and back in via the CoF icon in the top left.

---

### Post by ranch hand on 2010-06-14
I installed the sucker and it didn't explode.  That makes me happy.

Where is the documentation on this thing.  The help icon I removed from the launcher as useless as it is for the Ubuntu Desktop.

Looking in the gconf-editor it appeared to me that alt+F1 should get me a real menu.  Is this correct?

It does not.  Is there a way to get a real menu?

If there is a way to get a real menu I would say this is a pretty nice setup, particularly compared to GS.  Without a menu both are worthless as **** on a boar hog.

Besides the menu business I think that I could really get to like the setup on this.  Over all pretty nice.

Ah, the other thing I want to know.  How do you add things to the launcher?  I could not figure that out at all.

---

### Post by zekopeko on 2010-06-15
> **ranch hand said:**
> I installed the sucker and it didn't explode.  That makes me happy.

Where is the documentation on this thing.  The help icon I removed from the launcher as useless as it is for the Ubuntu Desktop.

Looking in the gconf-editor it appeared to me that alt+F1 should get me a real menu.  Is this correct?

It does not.  Is there a way to get a real menu?

If there is a way to get a real menu I would say this is a pretty nice setup, particularly compared to GS.  Without a menu both are worthless as **** on a boar hog.

Besides the menu business I think that I could really get to like the setup on this.  Over all pretty nice.

Ah, the other thing I want to know.  How do you add things to the launcher?  I could not figure that out at all.

I suggest you read [SABDFL's post ]("http://www.markshuttleworth.com/archives/383") to get a better picture of what is planned.

The menu is going to come later in the cycle. For now you can open the Applications folder (it should be on the dock unless you killed it already :D ). Start applications from there and then simply right click on the icon that appears in the dock. Dragging the .desktop files from the Applications folder crashes the dock and panel (at least for me).

Almost forgot; clicking on the Circle of Friends acts as compiz's scale plugin.

---

### Post by ranch hand on 2010-06-15
I found the applications applet and it does work after a fashion, a slow fashion.

I kind of like the Ubuntu Logo function.  I avoid compiz but this reminds me of the "activities" corner in GS without the BS.

If I can get anything to stick in the launcher panel it would be great, am about to go there now and fool with it.  That would cure, in one way, the need for an active menu.  I installed gnome-main-menu  by chroot from here and want to see if I can stick it on there.

I reread every thing I could last night before going to bed and have done some studying this morning between other activities and think I have  a better grasp of what I am doing.  This really could be a lot nicer than GS to use.

---

### Post by MacUntu on 2010-06-17
Right now you should call it 'Crashity'. :-\"

---

### Post by MacUntu on 2010-06-25
1.) How exactly do I start the expose/window overview mode after the recent update? 

2.) According to [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/598296](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/598296) I should have "places" when clicking on the Ubuntu logo, but all I get is a dark desktop and an apparently functionless search bar.

[img]http://img.xrmb2.net/images/209842.png[/img]

---

### Post by MacUntu on 2010-06-25
@ 1.) Seems (currently) not possible.
@ 2.) You need the packages unity-place-files and unity-place-applications

---

### Post by cariboo on 2010-06-25
You need to install the unity-place-files and unity-place-applications packages. As suggested in bug #[lpbug]598296[/lpbug].

---

### Post by MacUntu on 2010-06-25
You are ten hours too late. ):P

---

### Post by ankspo71 on 2010-06-26
Here are some screenshots of Ubuntu Netbook Edition:
[http://www.webupd8.org/2010/06/unity-launcher-looks-gorgeous-ubuntu.html](http://www.webupd8.org/2010/06/unity-launcher-looks-gorgeous-ubuntu.html)
Looking good!

---

### Post by ranch hand on 2010-06-26
There are screen shots on this forum, in this thread;

[http://ubuntuforums.org/showthread.php?t=1479298](http://ubuntuforums.org/showthread.php?t=1479298)

We have been testing it for a while.

It is very nice even on my desktop box.

---

### Post by MacUntu on 2010-06-26
Still has a long way to go, but looks very promising.

---

### Post by ankspo71 on 2010-06-27
Thanks for the link. I did glance through that link prior to posting but as I was glancing didn't see any screenshots that showed the white on the desktop, so I assumed the white part was a brand new feature that not many people knew about yet. Apologies for starting a second discussion. Yep, I can see that parts of unity aren't actually working yet. I tried it out last night.

---

### Post by cariboo on 2010-06-27
Merged threads.

---

### Post by x-shaney-x on 2010-06-27
I have a couple of issues:

Firstly:
I don't quite understand how I am unable to run the unity session from GDM (white screen)and running from within a gnome session leaves me with an unusably laggy desktop, unless run with the vblank=0 workaround, yet the daily iso images have been running perfectly (well, as well as unity can at the moment).

Secondly: I thought I would try a more up to date daily but the iso's dated 24th and 27th June have refused to boot, leaving me with kernel panic messages.
Is anyone aware of any problems with the daily's or is it a problem my end?
I did download both images twice and have tried burning them to 3 different USB sticks).

---

### Post by Skaarg on 2010-06-28
I recently installed 10.10 alpha and unity on my netbook since 10.04 was having issues with my touch screen. anyways I have one issue with Unity I was curious if there is a fix for. When I try to run a pinned program that needs elevated privileges such as synaptic package manager. It will not start the program with elevated privileges thus meaning I can't install anything, unless I start the program from /usr/share/applications. Is there anyway I can change settings for the launcher so it will start properly?

---

### Post by ranch hand on 2010-06-28
> **Skaarg said:**
> I recently installed 10.10 alpha and unity on my netbook since 10.04 was having issues with my touch screen. anyways I have one issue with Unity I was curious if there is a fix for. When I try to run a pinned program that needs elevated privileges such as synaptic package manager. It will not start the program with elevated privileges thus meaning I can't install anything, unless I start the program from /usr/share/applications. Is there anyway I can change settings for the launcher so it will start properly?
I thought maybe I was the only one this irritated.

I open mine from terminal instead of applications but none the less it is kind of silly not to be able to open from the launcher.

---

### Post by MacUntu on 2010-06-28
Make change happen: [https://bugs.launchpad.net/unity/+filebug](https://bugs.launchpad.net/unity/+filebug)

;)

---

### Post by ranch hand on 2010-06-28
> **MacUntu said:**
> Make change happen: [https://bugs.launchpad.net/unity/+filebug](https://bugs.launchpad.net/unity/+filebug)

;)
OK, so I keep hollering the same thing.  Sometimes it is good to get hollered at.  I filed on it like a good boy.

---

### Post by MacUntu on 2010-06-28
Good boy! =D>

Don't forget to post the link to the bug report, though: [https://bugs.launchpad.net/unity/+bug/599298](https://bugs.launchpad.net/unity/+bug/599298) :P

---

### Post by ranch hand on 2010-06-28
That is what happens when you do things at 3 in the morning because you can't get back to sleep after a family emergency.  What a night.  Wife and I are both whipped and have decided that having relatives is a big mistake.

---

### Post by MacUntu on 2010-06-28
> **ranch hand said:**
> having relatives is a big mistake.
It's fine as long as they are far away. :lolflag:

---

### Post by DanaG on 2010-06-30
Say, is this Unity thing supposed to give me a totally blank desktop, with only the icons on the left, and no visible way to start anything not listed?  When I click the "menu" thingy -- and by the way, I think having the window manager draw the panel is bad design! -- I get a search box, with the text "Search" that can't be changed.

---

### Post by ranch hand on 2010-06-30
You should have two options if you click on the logo in the upper right corner.  The one on the right should give you an applications menu.

If you are not seeing everything it might be a good idea to get the xorg edgers ppa and use those drivers.  I had too.  Do not know if it would work for you but I would give it a shot.

---

### Post by DanaG on 2010-06-30
What else is weird, that I doubt new video drivers will fix: when I minimize Namoroka, and then click the icon on the "taskbar", it creates an additional window, instead of unminimizing.   The same thing happens even when I don't minimize it.  In fact, it doesn't even show the "app is running" arrow overlay.
EDIT: Also, that search box is now accepting input, but rather stupidly, the "Search" text doesn't go away when you start typing -- so you end up with it saying:
Searchfirefox

---

### Post by x-shaney-x on 2010-06-30
I think at this stage, the new apps and places dropdowns/tabs/panels are mainly placeholders to show how it is going to be in the future.

I don't think anything about unity can really be considered desktop (or should that be netbook?) ready just yet.

Think of it as nothing more than a preview for now, functionality will follow.

---

### Post by MacUntu on 2010-06-30
DanaG, make sure you have the packages unity-place-files and unity-place-applications installed. The search bar thingy is already filed.

> **x-shaney-x said:**
> Think of it as nothing more than a preview for now, functionality will follow.
I think it's pretty much usable right now. It's just far away from being finished/feature complete.

---

### Post by ranch hand on 2010-06-30
> **MacUntu said:**
> DanaG, make sure you have the packages unity-place-files and unity-place-applications installed. The search bar thingy is already filed.


I think it's pretty much usable right now. It's just far away from being finished/feature complete.
There are a couple of things, that I think they will get, that I want to see but right now I would say that anyone that wants an alternative to Gnome Shell has one right here.

It is a little different than what i am used to but quite functional and usable without a lot of silly effects that simply slow you down.

I prefer the current Gnome desktop with panels but Unity is very nice.  I could use that all the time.

---

### Post by zekopeko on 2010-06-30
> **DanaG said:**
>  When I click the "menu" thingy -- and by the way, I think having the window manager draw the panel is bad design! -- 

You're talking about GnomeShell. Mutter (the window manager used in unity) doesn't draw the panel.

---

### Post by frustphil on 2010-07-01
Am I the only one experiencing this bug?



Look at the tilted icons at the bottom end of the launcher, they're barely visible... And if you look at the lone tilted icon at the top, it looks like it's a rendering glitch. How much more if it's the only tilted icon on the launcher...

---

### Post by zekopeko on 2010-07-01
> **frustphil said:**
> Am I the only one experiencing this bug?

Look at the tilted icons at the bottom end of the launcher, they're barely visible... And if you look at the lone tilted icon at the top, it looks like it's a rendering glitch. How much more if it's the only tilted icon on the launcher...

The launcher is extremely buggy at this time. Report a bug.

---

### Post by x-shaney-x on 2010-07-01
How did you add apps to the launcher? I haven't been able to drag anything to it (though I haven't fiddled around with it much).

---

### Post by nilarimogard on 2010-07-01
@x-shaney-x: when an application is running, just right click it and select "keep in launcher"

---

### Post by stoneguy on 2010-07-01
If you're going to work with the netbook edition, be sure and get into the shell and do an update-manager as soon as the 1st boot completes. The system as delivered comes with an empty System folder and various other oddities. This update will get you to where you have something testable and you can discover the A2 UI changes :confused:

ASUS 1005HA, 2GB

---

### Post by x-shaney-x on 2010-07-01
> **nilarimogard said:**
> @x-shaney-x: when an application is running, just right click it and select "keep in launcher"
Hehe, so simple.  I can now get into trying it out properly.
Just wondering, does anyone know if it's currently possible to set the window manager to compiz when using the unity session?
I find mutter very slow and horrible in so many ways (and worse on maverick than lucid with une PPA) but everything is much better if I launch unity while compiz is running in my gnome session.
Trouble is I'm then stuck with a gnome panel I don't want.

---

### Post by cariboo on 2010-07-01
There is a thread about UNE already called the Unity thread. Most of us are aware of the problems. Moved to the Unity thread.

---

### Post by Dragonbite on 2010-07-02
Where did my Unity go?

I installed Unity, but it hasn't been working on my system (once the mouse goes over the left side panel, it keeps blanking-and-refreshing the screen at every mouse movement or click but I think part of this is the Intel 855 issue).

I tried, since things are getting better and better in the Intel graphic department (have had almost full capability including desktop effects, which I've NEVER had work before), to give Unity a try, but now I can't find it!

I don't see it listed in my available desktops, nor in the Desktop Effects controls.  Did it get moved?

I've been enjoying using Gnome-Shell in Fedora 13, but still want to try Unity.

---

### Post by nilarimogard on 2010-07-02
> **x-shaney-x said:**
> Hehe, so simple.  I can now get into trying it out properly.
Just wondering, does anyone know if it's currently possible to set the window manager to compiz when using the unity session?
I find mutter very slow and horrible in so many ways (and worse on maverick than lucid with une PPA) but everything is much better if I launch unity while compiz is running in my gnome session.
Trouble is I'm then stuck with a gnome panel I don't want.

Most probably yes, but I haven't tried it. Try running "compiz --replace"

---

### Post by x-shaney-x on 2010-07-02
> **nilarimogard said:**
> Most probably yes, but I haven't tried it. Try running "compiz --replace"
If I run compiz --replace then unity dies.
If unity is launched AFTER compiz then everything is ok.

The only way I can find is to actually add unity to my startup programs but it acts a bit wierd then and doesn't seem to save changes (apps added).

For now it works out ok-ish because I use the gnome panel with unity with only cardapio on it because I need a decent menu but once the built-in unity menus start working I won't need the panel and I don't believe there is a way to disable it.

So ideally I want to run compiz within the unity session.
I can't remember where the session startup scripts are located because I may be able to add compiz before unity.

---

### Post by x-shaney-x on 2010-07-05
Just wondering about the places and application panels.
The impression I get from reading various things is that the file manager part is supposed to actually show files at this stage.
I have unity on my laptop lucid install (via PPA) and on my meerkat install and I also have it installed on a netbook and the files don't show on either.

The applications do show though but not the search, not sure if that is enabled or not yet.

---

### Post by ranch hand on 2010-07-13
Wow, after updating today the bugger looks almost ready to use.

Can open apps requiring a login box to pop up (synaptic, gparted, etc) from the menu instead of having to use the terminal.

File menu still not there.

I am so impressed that I have installed my bookmarks on here so I can spend more time on here.  This is looking really good.

---

### Post by frustphil on 2010-07-23
Does anyone find it annoying when you hover/click on a non-tilted icon and then it slides up/down after you move away your mouse? IMO, non-tilted icons shouldn't behave like that. Because when you launch two non-tilted apps successively and decide to switch to the first launched app, you would normally expect that it's on the same position where you left after clicking. Currently, you will have to find it again. I would understand if the second icon you click/hover is a tilted one because you would obviously need room for it to expand and, in effect, pushes the first icon up/down. Is such behavior part of the spec? I hope you guys get my point.

---

### Post by ranch hand on 2010-07-23
I have an interesting thing happening for the last few days.  Can't log into the Unity session at all.  Just a white screen.

The interesting part is that Ubuntu Desktop and a 64 bit kernel bot installed.  The kernel probably accounts for my failure to get Unity to work.

This was installed with the CD for UNE only available in 32 bit.  Have no idea how this got changed or even how to file a bug on it as I really do not have a clue what happened.

Just thought I would share that.  I do ISO testing and A3 is coming right up so I will reinstall when the ISO RC (Monday or Tuesday) becomes available.  Kind of weird.

---

### Post by cariboo on 2010-07-23
I've got a new icon at the bottom of the panel, and I don't know how it is supposed to work, you click on it, the screen turns black, any app that is open disappears until you click on it's icon, and it seems to to zoom out.

---

### Post by Framli on 2010-07-23
It's an early buggy iteration of the workspace switcher.

---

### Post by zekopeko on 2010-07-23
Anybody know when 0.2.20 is going to land for Lucid?

---

### Post by x-shaney-x on 2010-07-24
Adding apps to the panel is a bit quirky at the moment too.
If I launch an app, there is no option to keep in launcher.
If I drag the icon out and move it up the launcher then it automatically pins it and it now has an option to keep in launcher (which is already checked now).

Very happy to see the app switcher back, which I presume will be used to both switch apps and workspaces, a little like gnome-shell.

Doesn't do much yet but you can see the point.

They have also turned off the application menubars now as well.  I would generally say the appmenu is fully working, if a little flaky with certain apps (emesene, gimp) and slow with nautilus.
Although I still doubt I will ever use it and will turn window menus back on.

But I would say unity is starting to shape up nicely and I can't wait for the finished thing.

---

### Post by zekopeko on 2010-07-25
I just upgraded to Maverick. When did the snake-skin background of the launcher go? It's still there when you launch applications (the glow around the app icon).

---

### Post by x-shaney-x on 2010-07-25
The background to launcher went after the last update (Thursday).
I rather liked it.  What they should do is make the panel look like the desktop is slightly above it gives the impressions it has been slid across to show the launcher (or even actually do that as a flashy autohide.

Something like the Mac OS 10 dashboard panel.  Love or hate Mac, that panel is sexy.

---

### Post by zekopeko on 2010-07-25
> **x-shaney-x said:**
> The background to launcher went after the last update (Thursday).
I rather liked it.  What they should do is make the panel look like the desktop is slightly above it gives the impressions it has been slid across to show the launcher (or even actually do that as a flashy autohide.

Something like the Mac OS 10 dashboard panel.  Love or hate Mac, that panel is sexy.

Definitely intentional.

[https://bugs.launchpad.net/ayatana-design/+bug/607816](https://bugs.launchpad.net/ayatana-design/+bug/607816)

---

### Post by DanaG on 2010-07-30
Say, my Unity is rather useless.
When I type in the search box, letters appear.  That's it.  Nothing else happens.  Ever.

---

### Post by go7Ul1ai on 2010-07-30
> **DanaG said:**
> Say, my Unity is rather useless.
When I type in the search box, letters appear.  That's it.  Nothing else happens.  Ever.

Because it's a work in progress :)

---

### Post by Universal344 on 2010-07-30
Hey just wondering if anyones Unity looks like the screenshots in this blog post, or whether its coming in an update soon.

[http://www.omgubuntu.co.uk/2010/07/unity-as-of-now.html]("http://www.omgubuntu.co.uk/2010/07/unity-as-of-now.html")

---

### Post by go7Ul1ai on 2010-07-30
> **Universal344 said:**
> Hey just wondering if anyones Unity looks like the screenshots in this blog post, or whether its coming in an update soon.

[http://www.omgubuntu.co.uk/2010/07/unity-as-of-now.html]("http://www.omgubuntu.co.uk/2010/07/unity-as-of-now.html")

The current version doesn't look like those on the screenshots, an update should have been pushed on thursday but hasn't so it's safe to say that an update should be on its way soon.

---

### Post by x-shaney-x on 2010-07-30
I actually doubt the next update will look the screenies there, at least not if it get updated in the next few days.
There was a bit of a discussion going on in that article between me and a couple of others as to whether or not those screenies were mockups.

I now think they are probably real but more a devs experimental version :)

---

### Post by cariboo on 2010-07-31
Usually omgbuubntu is wrong more often than they are right, although we are getting pretty close to those mockups.

---

### Post by MacUntu on 2010-07-31
The other day I started to play around with the files in /usr/share/unity/themes and when I changed the panel_background.png to a light color, I found this:

[IMG]http://img.xrmb2.net/images/443786.png[/IMG]

I guess that dark line at the bottom of the panel is not supposed to be there. After opening and closing the files/apps overlay it's even covering the CoF area:

[img]http://img.xrmb2.net/images/438306.png[/img]

If you see this too, please confirm: [https://bugs.launchpad.net/unity/+bug/611002](https://bugs.launchpad.net/unity/+bug/611002)

---

### Post by tjeremiah on 2010-07-31
would like to finally test but tried to get it to run in Vitrualbox and cant get it to run. Like one said months ago, all I get is the desktop  image to load and thats about it.

---

### Post by KdotJ on 2010-08-01
> **tjeremiah said:**
> would like to finally test but tried to get it to run in Vitrualbox and cant get it to run. Like one said months ago, all I get is the desktop  image to load and thats about it.

I still can't get it to run on my netbook... lol

---

### Post by ranch hand on 2010-08-01
I had trouble with it on the desktop.  Installed the xorg edgers ppa and those drivers made it work until it got corrupted last week.

Clean install with the A3 RC ISO coming right up here in ISO testing.

---

### Post by nilarimogard on 2010-08-03
> **ranch hand said:**
> I had trouble with it on the desktop.  Installed the xorg edgers ppa and those drivers made it work until it got corrupted last week.

Clean install with the A3 RC ISO coming right up here in ISO testing.

Hmmm make sure you don't add the Gnome Shell PPA - that breaks Unity.

---

### Post by ranch hand on 2010-08-03
No I did not add the GS ppa.  I actually install Unity in the first place to see what kind of options one would have in a GS by default Desktop world.

Unity is a much better approach, to me, than GS.  A bit rough but with coherent goals and a desktop that is already usable.  I kind of like it.

I ran the edgers drivers because they allowed me to see the launchers on the panel for about a month.

Got an update and seemed to have some 64bit kernel stuff creep in.

Down loading the A3 RC ISO right now.  Kind of excited.

---

### Post by x-shaney-x on 2010-08-03
From the various mockups of both and current development in unity, I can't help but feel unity and shell will pretty much be the same thing.

---

### Post by shafin on 2010-08-03
^^^Except one is able to run unity and compiz concurrently, which is a huge win for me. For that reason alone, I'd go with unity.

---

### Post by x-shaney-x on 2010-08-03
^^^Really?  I have been having trouble running compiz with unity lately, all sorts of wierdness happens.

For now I'm just poking around and keeping an eye on unity, doubt I'll be using it full-time just yet.

---

### Post by ranch hand on 2010-08-03
I am bummed.  A3 just gives me a blank white screen when I boot.  Oh well, have other things to test so will have to put this on hold for a while.

---

### Post by fuzetsu490 on 2010-08-04
> **tjeremiah said:**
> would like to finally test but tried to get it to run in Vitrualbox and cant get it to run. Like one said months ago, all I get is the desktop  image to load and thats about it.

same issue here, I tried to run it on virtualbox but i get nothing but the wallpaper, not even a cursor...

---

### Post by shafin on 2010-08-04
Unfortunately mutter does not play nice with virtualbox. You'll need to install unity on a real installation to test it.

---

### Post by fuzetsu490 on 2010-08-04
i see, thanks.

---

### Post by Tompalaz on 2010-08-16
I'm sorry if someone already asked these questions.

1) How do I add more workspaces, I currently only have one.
2) The application folder/viewer doesn't show all my applications. VirtualBox won't show up if I search for it.

---

### Post by cariboo on 2010-08-16
There is no way to add workspaces in Unity yet. The applications folder, is still a work in progress,

---

### Post by x-shaney-x on 2010-08-16
On maverick I have the old intel white screen problem again since the last couple of updates.
It still runs on lucid from the PPA but I notice the PPA hasn't had the recent updates maverick has :(

---

### Post by MacUntu on 2010-08-16
I'm not sure if it's planned to add workspaces? I was under the impression that the maximized applications *are* your workspaces.

---

### Post by ktp on 2010-08-16
> **MacUntu said:**
> I'm not sure if it's planned to add workspaces? I was under the impression that the maximized applications *are* your workspaces.

That kind of makes sense...at least for unity.

---

### Post by cariboo on 2010-08-16
I personally don't think the devs are going to add extra workspaces either, but I believe the that workspace switch icon in the panel is supposed to do be a work-alike.

---

### Post by MacUntu on 2010-08-22
> **MacUntu said:**
> I'm not sure if it's planned to add workspaces? I was under the impression that the maximized applications *are* your workspaces.

Stupid me, my number of workspaces was 1, so I obviously never saw any workspaces when clicking the workspace switcher. :lolflag:

---

### Post by ranch hand on 2010-08-22
I am going to try installing the thing again.  Last time it just would not work (got a nice white screen but it bored me so put something else on there).

Got to see where it is at now.

Wish they would get GS building right so I could put it on somewhere too.  Didn't like it enough to go to all that much trouble.

I would like to compare it and Unity on real installs that at least try to work.

Unity still looks like a better choice to me.

---

### Post by ranch hand on 2010-08-26
The daily for today actually held up long enough to log out on its own and I could then login the desktop.

Got the installer up and got to the partitioner and it just crashed when I tried to "change" a partition.

This is a bummer.

Guess I will just try installing Unity on an existing desktop install.  Might be best anyway as I have one with the edgers drivers installed on it anyway.

---

### Post by ranch hand on 2010-08-26
I guess I need to scratch Unity for the time being.

Installed on existing desktop.  Booted to it.  Flashes from white screen to wallpaper and back very rapidly.  That is it.  Tty to reboot.

Then try GS from the repo on the same OS.

GS from the repo does not work that well.  When I try to switch to it the box just freezes up hard.  Have to unplug the bugger to get out.

Desktop works great.

---

### Post by ranch hand on 2010-08-27
The upgrades have changed things.

Now all I get is a white screen and tty does not work.  Alt+SysRq+b does.

I have todays ISO and will try to install it.  It is working at a disadvantage because I am trying to install after booting to the ISO.

Did not work from the same drive (not surprised) so I will be copying to another drive and try it later tonight.

---

### Post by ranch hand on 2010-08-28
I have a clean install of UNE on its very own partitions and the Ubuntu Desktop session works great.

Should I quit trying to get Unity to run?  Is my 2 year old box just too old to run it?  This appears to be the case with GS.

The blank white screen is, I will admit, a huge improvement over the default wallpaper.

---

### Post by godhika on 2010-08-28
I think the problem is the Radeon card if that is the configuration you try setup Unity. Currently Unity is not running with the open source driver (there is a bug report somewhere)

---

### Post by ktp on 2010-08-28
> **ranch hand said:**
> The blank white screen is, I will admit, a huge improvement over the default wallpaper.

Seeing the bright sides of everything =)

---

### Post by ranch hand on 2010-08-28
> **godhika said:**
> I think the problem is the Radeon card if that is the configuration you try setup Unity. Currently Unity is not running with the open source driver (there is a bug report somewhere)
Ah, that would be it then.  I will just leave the bugger there and hope for an upgrade.

---

### Post by Madspyman on 2010-08-29
Just tried Unity in my Maverick partition and was greeted with garbled graphics followed by being booted out to the GDM login. I just had a similar experience with gnome-shell, I'm guessing it must have something to do with mutter.

---

### Post by cariboo on 2010-08-29
I'm not sure if it's still the same, but unity did use a different version of mutter than gnome-shell. If you are going to try unity on the same system as gnome-shell, you have to purge one of them before installing the other.

---

### Post by KdotJ on 2010-08-29
> **ranch hand said:**
> The blank white screen is, I will admit, a huge improvement over the default wallpaper.

Lol that is a killer line

---

### Post by Madspyman on 2010-08-30
> **cariboo907 said:**
> I'm not sure if it's still the same, but unity did use a different version of mutter than gnome-shell. If you are going to try unity on the same system as gnome-shell, you have to purge one of them before installing the other.

I did purge gnome-shell before I installed Unity. I purged shell earlier when it wasn't working. It's no big deal though I'm not planning on really ever using Unity I just wanted to see what it was like.

---

### Post by ranch hand on 2010-09-07
I thought I would be clever and booted to this Unity install.  Stopped by bios on the way here and switched fro my ATI card to the onboard intel video controller.

Not so clever.  Exactly the same deal.  Nice white screen.

I am truly bummed.

It does change some things though.  Over on the GS install when I try to get GS to run I no longer have to tty to get out.  gnome-shell --replace just kicks me back to login.

---

### Post by DanaG on 2010-09-10
Here's my Unity, after doing (from a tty) compiz --replace, and killing unity to let it respawn.
Note that nothing reponds to clicks -- not even the indicators.
This is on my GMA950 netbook.
Attachments are a screenshot and a console log of Unity.

EDIT again: I ppa-purged Edgers, and at least now it displays something.... but it flickers to bright white every once in a while when idle, and spazzes out (strobes white) whenever I mouse over anything.  I'm glad I'm not epileptic -- that thing needs a warning sign on it!

---

### Post by Half-Left on 2010-09-10
Not sure why people keep comparing GNOME Shell with Unity, since they're totally difference interfaces. Unity is purely a netbook interface, GS is not.

Unity seems pretty good though for a netbook interface.

---

### Post by x-shaney-x on 2010-09-10
@  DanaG

Unity has had intel related problems causing flickering.
I had not been messing with unity recently because of it but I installed from a daily recently without copying anything from my home directory and it was working without any flickering and such.
After copying my home back it started flickering again so it seems some settings somewhere were causing problems.
Might be worth temporarily moving your home directory to see if it helps?

@ Half-left

Though they may be designed for different purposes, there is no getting away from the similarities of shell and unity.
Looking at the current crop of mockups they look like they will be getting even more similarities and are basically heading in exactly the same direction.
At the end I think the only big difference will be the combined panel/appmenu/window decoration in unity.

<EDIT>
Todays updates seem to introduced some regressions.
Half my launchers on the side panel have vanished.
Many apps now have to be opened twice, the first time it pops up then instantly closes, opening it a second time keeps it open.
Removing the unity stuff in .gconf hasn't helped.

---

### Post by tjeremiah on 2010-09-10
I managed to get it to work by installing it via wubi and so far, I dont like it, right now. How do you hide the bar to the left? But in its current state, I dont see myself installing this on my mother's netbook. She finally got comfortable with Netbook Edition and this unity appears to be a lot more confusing to use.

---

### Post by Half-Left on 2010-09-10
> **x-shaney-x said:**
> @ Half-left

Though they may be designed for different purposes, there is no getting away from the similarities of shell and unity.
Looking at the current crop of mockups they look like they will be getting even more similarities and are basically heading in exactly the same direction.
At the end I think the only big difference will be the combined panel/appmenu/window decoration in unity.

They may look similar but GNOME Shell isn't a one size fits all netbook interface and much more flexible for themes than Unity.

Does Unity even use CSS?

---

### Post by x-shaney-x on 2010-09-10
I agree unity seems more of a "take it or leave it" thing.

---

### Post by cariboo on 2010-09-13
I saw [this]("http://www.reviveyourpc.ie/unity/welcome.html") on the Ayatana mailing list this morning. Unity+1?

---

### Post by Merk42 on 2010-09-13
> **cariboo907 said:**
> I saw [this]("http://www.reviveyourpc.ie/unity/welcome.html") on the Ayatana mailing list this morning. Unity+1?It's just some person's well done, and slightly interactive, mockup. Nothing official, and I hope not with the way that dock disappears.

---

### Post by cariboo on 2010-09-13
If you click on the ubuntu icon in the top left corner, it minimizes the app and shows the dock again. Yes I realize it's just a mockup, but sometimes these things become reality. Sceenshot 0 is nautilus full screen and screenshot 1 is the quick app switcher.

---

### Post by MacUntu on 2010-09-14
Three words: do not want. :)

---

### Post by 23meg on 2010-09-15
People having performance problems, take note:

[http://twitter.com/kamstrup/status/24585303692](http://twitter.com/kamstrup/status/24585303692)

---

### Post by cariboo on 2010-09-15
> **23meg said:**
> People having performance problems, take note:

[http://twitter.com/kamstrup/status/24585303692](http://twitter.com/kamstrup/status/24585303692)

Thanks for the heads up 23meg.

---

