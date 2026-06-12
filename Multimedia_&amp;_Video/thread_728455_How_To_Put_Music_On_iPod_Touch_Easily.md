---
title: "How To Put Music On iPod Touch Easily"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by deltaandroid on 2008-03-18
Ok, if you are anything like me then you have spent tireless hours, and frankly too much time trying to get music onto your iPod touch in Linux. Well, I have used Ubuntu, (I currently use Fedora), but this tutorial is probably easier even in Ubuntu (Hence the forum I'm posting in).

Warning; I take no responsibility whatsoever for any damages or other error that results on your computer, iPod, or body. Thanks.

Well, first you will need the fuse tools, so just go ahead and install fuse-utils, you can get the .deb somewhere or just apt-get it.

sudo apt-get install fuse-utils
sudo apt-get install sshfs

Punch that into your terminal, and let it install, saying yes or "y" whenever necessary. This program will allow you to mount a ssh filesystem.

Nextly, you gotta do the iPod side of things. You will need to get your iPod jailbroken, and then install the SSH system and BSD subsystem and finally MNPLight from the installer.app repositories.

Then go into your ipod touch and go to the settings>general. When there, set the "auto-lock" to "never". You must do this everytime you wish to add more music. Then go hop onto your Wifi.

Where it displays your SSID of the network you connected to, touch the little arrow to the right of it. This will show you your iPod's network IP adress. You may want to set this to static on your wireless router so that you do not have to check everytime, I don't, but its up to you.

Next you will have to go back on your PC, and open up the Terminal. You can do the rest without super user privledges.

Most people have trouble at this point because of all the command line input, but by using a readily available and privledged desktop location, you only need 3 commands for the whole process.

Make a folder on the desktop, its best to name it 'ipod' or you will have to improvise on the commands I tell you. The below code is one way of doing this:

cd /home/<YOURUSERNAMEHERE>/Desktop
mkdir ipod

Now, it is time to test out the powers of the Fuse-Utils!!!!!

Get the touch's IP handy. Now, still in terminal (ok, the last part was terminal optional, you could have done it via GUI.)  put in this command  

sudo sshfs root@<IPODIPHERE>:/ /home/<YOURUSERNAME>Desktop/ipod

It will then ask you for a password. The password 1.1.0 Touch  is 'dottie', and for 1.1.1 and 1.1.2 Touch it is 'alpine'.

Once this is done, if everything is successful it will just return to the basic terminal.

Now on your desktop, you will see a folder called ipod, this is the contents of your ipod (until disconnect). You should open it and then navigate to /var/root/Media.

In that directory, if one does not already exist, create a folder called "MNPlight". Then inside it create a folder called "music". Both of those are case sensitive BTW.

Inside that folder, put all the music files (.mp3) that you want to download/upload to the Touch.

After that, you can disconnect the ipod with 

fusermount -u /home/<USERNAME>/Desktop/ipod

When that is complete, go to your Touch, and execute the MNPlight application. You can then go to "Playlists", and then below it will display a directory, you can then touch the "import" button. This will reload the page and import all the songs.

You can then find them on your touch via playlists and MNPlight* (the star will increase numerically everytime you import songs. Theses are also present in your library on the touch, so congratulations, with any luck, you have all your new music using Ubuntu!

If this helped anyone at all, then I am very pleased. I myself spent countless hours working at this, and i probably still be if those that coded "MNPlight" never came along. That is why I decided to make this tutorial, its my first, so any forum elders go easy on me if you find any errors.:)

Post any questions or comments, and I will be sure to reply soon.

---

