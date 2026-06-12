---
title: "World of Warcraft Extreme Problem Committee ASSEMBLE!!!"
date: 2009-08-01
forum: Multimedia Software
---

### Post by domezone on 2009-08-01
So first off let me say i really enjoy running ubuntu. I feel it just has more of a personality then that of other major brand name pc based operating systems of the windows flavor. That being said ive spent about 4 days researching to fix this myself as i am not exactly a veteran linux user, but to no avail. I fixed a previous problem with ventrilo broadcasting static ear bleeds to my friends but now im stuck on WoW

My graphics card isnt the most amazing, its a radeon x1050. I have no problem playing wow for 10 hours if i wanted to on it within windows xp or vista. The problem lies within ubuntu. The installation was a hassle but nothing i couldnt survive through in hopes of completely getting rid of windows partition but now im stuck :(

Run WoW in both opengl and directx mode, while in directx it appears spectral lighting is on though i dont have it enabled and actually gives WoW a crazy glow that makes it look cool, but as soon as i log in it looks wonderful until i attempt to alter the camera view, then boom my video card stops sending a signal to my monitor and it goes blank and a repetative stuck noise is then heard. In opengl everything looks normal though it just runs slower on login, then when i login same problem i then have to completely reboot.

I didnt change any drivers my first go at it but rather just entered all the diff settings in the wow config file attempting to fix the problem to no avail. I then tried to install the envyng ati drivers which caused a world of problems to where i couldnt even log into ubuntu. i had to recovery mode it and delete the driver through there just to get into my computer again. After that it seemed that xserver no longer detected my video card like it once had.

It started out by saying the name and what not and all the info on it but now that i uninstalled the other driver and followed the normal procedure to reinstall the mesa lib things it no longer showed my graphics card in xorg.conf

i figured mabey i could just manually input the driver i wanted it to run on so i went ahead and did that. I used the ati driver the radeon driver and the vesa driver like that and each replicated all previous problems in both opengl and directx

i cant get the damn thing to stay on wow for longer then like 10 seconds before not just a crash but a complete shutdown of the system is required because my video card stops talking to my computer and just shuts off.

huge post i know but i wanted to go in depth on the problem. My xorg.conf isnt of any use i dont think as it just displays the general info it puts out when it doesnt detect anything.

my wow config file has all the usual things you would put into it to make it work. nothing has changed. thanks for any responses ill be checking frequently.

---

### Post by Doctor Debian on 2009-08-01
Use FGLRX for playing wow, the open source alternatives unfortunately don't compare.

EDIT: Forgot to say to use this in opengl mode for best performance.

This should fix your problem;

Open the registry editor (type regedit in terminal) and navigate to the following key

HKEY_CURRENT_USER\Software\Wine\

Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder.

Right-click on the wine folder and select [NEW] then [KEY]

Replace the text New Key #1 with OpenGL

Right-click in the right hand pane and select [NEW] then [String Value]

Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)

Then double click anywhere on the line, a dialog box will open.

In the value field type GL_ARB_vertex_buffer_object

Copied from WineHQ. Fixed the problem for my on my Acer laptop.

---

### Post by domezone on 2009-08-01
i tried using the fglrx driver but like i said i couldnt even boot into ubuntu with it installed. i did aticonfig --initial -f and i got an error that there was no device recognized when running through recovery console.

i tried to install the actual catalyst stuff from ati website but i get an error in the terminal when i try to run that, somthing about my kernal being uncompatible or somthing.

the only option i really have is the ati,radeon, or vesa driver. From what i can tell radeon looks the best but in opengl with that registery along with anything else i could find on the net in diff config files it still crashes on start up and am forced to reboot.

mabey my gfx card just isnt supported enough through the default drives and the proprietary seem to be for newer cards and not mine. just **** out of luck? guess its back to windows if thats the case.

---

### Post by domezone on 2009-08-06
Well, since noone knew an answer to this i finally figured it out myself. The reason version 9 of ubuntu wont play wow right on the x550/x1050 card is because the initially installed open source drivers dont support that card much in a 3d enviroment. Also you are not able to install the 9.3 proprietary drivers as the kernal only accepts 9.4 *i think*.

That being said if you want to play games on a x550/x1050 card you must install ubuntu 8 hardy or linux lime 5 hardy. there both LTS and you can install the 9.3 catalyst ati drivers.

Only problem with world of warcraft is that hardware curser isnt enabled in opengl so performance with mouse scrolling suffers, though there are some known work arounds blizzard refuses to actually fix this.

GL to everyone that gets it to work, once i installed hardy everything worked great.

*This might be the same for other cards but i know for sure the x550/1050 needs 9.3 as its support in through drivers only goes up to 9.3. If when you choose your card on the amd site it only lets you download 9.3 catalyst that means you will need hardy or lower linux distributions.*

---

