---
title: "[SOLVED] Help getting a TiVo remote working"
date: 2008-11-05
forum: Mythbuntu
---

### Post by sgtstadanko on 2008-11-05
I have a streamzap pc remote that I have configured with the control center. It works great but I would like to use my TiVo remote instead of the streamzap one.  Has anyone setup a Tivo remote with myth here and if so would you share your configurations (lircd.conf/lircrc) and experiences.

I tried with a series 2 config file i found on the internets but no love was had.  

thanks

---

### Post by sgtstadanko on 2008-11-06
ended up using irrecord to get this working.  in case anyone else needs the same, here is how I did it:

1. Killed mythfrontend and mtd as both had grabbed the lirc device

2. su - root

3. irrecord --device=/dev/lirc0 Tivo  (this may be different depending on your IR devices)

4. Follow learning directions...basically it has you press all the buttons for a second to determine the signal length, then it has you teach the remote buttons.  It asks you to name the buttons and press the button on the remote. 

5. When done, you are left with a lirc config file named Tivo. I copied this to the lirc remotes directory just to keep things in the same place.
mkdir /usr/share/lirc/remotes/tivo  && cp Tivo /usr/share/lirc/remote/tivo/

6. You could do this by editing the lircd.conf but I used the Mythbuntu control center to do it.  Launch Control Center and goto the IR section.  Select "Custom" from the dropdown menu and click on the Configuration and select remotes/tivo/Tivo.  I tried to use Generate dynamic Button mappings but that didnt work for me so you can leave that unchecked and do it manually.

7. Click Apply and let it write the changes.

8. Edit the ~/.lirc/mythtv file to put your mappings in.  Basically I used one that i had already had buttons mapped for a Streamzap remote.  All i had to do was replace the remote name eachtime it after the "begin" line for the button.  Since I named my remote config in step 3, "Tivo" I just did a global search and replace with vi.  This is case sensitive and wont work if you dont have it correct.  If in question look at the name in the file you generated in the irrecord step.  For each button/function i looked at what i named the buttons in the Tivo config file...for example instead of "Menu" for the Menu button on the remote to send the "M" character, I changed it to "Tivo" for the Tivo button on the remote.  When pressed it now sends the "M" signal and brings up the menu. Once again this is case sensitive so just refer to you Tivo remote config you made.

I am still adding new buttons and trying to figure out if can fake macros with it...like bringing up the program guide with one button.  Also need to do my mplayer lirc as well.  So far it works solid.  I have attached my config files but I recommend going the irrecord route as there a lot of different Tivo remotes..and you remote sends different signals based on what position the 1/2 switch is in.  Also this should work for any remote....not just Tivo

Enjoy...
Bill

---

