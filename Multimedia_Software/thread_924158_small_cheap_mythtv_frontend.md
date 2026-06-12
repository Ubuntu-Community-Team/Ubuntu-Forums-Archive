---
title: "small cheap mythtv frontend"
date: 2008-09-19
forum: Multimedia Software
---

### Post by oobe-feisty on 2008-09-19
Hi im looking for a solution for a small cheap mythtv frontend 

im considering buying a cheap second hand xbox and installing mythbuntu or xebian and was wondering if anyone had any input for me here are the things i need to consider.

1. my pc is a mythbackend and frontend in my bedroom connected over a 54g wireless setup i would like to add wireless functionality to the xbox apperently my only option is to add a usb 1.1 adapter which may be to slow for streaming playback ? ( i transcode my recordings so i know it uses less bandwidth) will this be an issue?

2. the ones im looking at on ebay dont come with xbox dvd remotes i was hoping to just get an mce usb remote and configure lirc as normal i havent found much info on this will this be suitable 

3. i dont plan on playing back HDTV so this will not be an issue 

has anyone had any experience with what im talking about any hints or suggestions would be appreciated

---

### Post by oobe-feisty on 2008-09-19
after doing some further reading i decided although this is possible i am better off getting a cheap pc solution instead as it will be much more hassle free

---

### Post by oobe-feisty on 2008-09-19
just bumping this thread cause i still havent decided on what hardware to get for a small sized pc i keep looking at nice looking small form factor pc's on ebay but the problem i keep coming across is a lot of them dont support normal gpu's and have very small power supplies 200W so a lot of GPU's will not be supported

---

### Post by oobe-feisty on 2008-09-20
bumping my thread again this is the latest question that no one will most likely comment on 

im deciding between 6200 or 5200 low profile cards for primarily displaying sd recording's but it will be linked to a plasma 42" 1080 capable tv and still want to be able to playback HD im leaning towards the 5200 cause it can use xvmc with a color osd but will get the 6200 if i need to in order to display at full 1080 resolution

the card will be going from DVI > HDMI not tv out

before suggesting i get some different card the pre requisite is that it is a low profile card and agp

EDIT: i just found somthing answering specifically what i wanted to know [http://www.mythtv.org/wiki/index.php/Configuring_HDTV#NVIDIA](http://www.mythtv.org/wiki/index.php/Configuring_HDTV#NVIDIA)

according to this both will display HDTV but the 5200 has odd display issues that can be resolved has anyone had any experience with this

---

### Post by paulg on 2008-09-24
What's "*cheap*"? :)

Lot's of people like the Mac Mini's. Can use an OSX front end or install Mythbuntu etc. I don't have any experience with them.

For your card question, I'd probably go with whatever is cheapest, but if you plan on running 1080i/p on a board that only has AGP then you're probably using an old processor and you may run into some trouble. Just to be clear xvmc will only work with mpeg2 and not some of the other formats out there (although if this is a frontend, you probably have a backend somewhere making recordings...). Not to discourage but there are limitations to what it can do. I have a 7600GT (AGP) that I've been struggling to get working properly with xvmc but I'm currently limited to SD only so my frontend/backend struggles along without it. It's not the easiest thing to configure, but probably less difficult than lirc!

---

### Post by oobe-feisty on 2008-09-25
> **paulg said:**
> What's "*cheap*"? :)
I'd probably go with whatever is cheapest, but if you plan on running 1080i/p on a board that only has AGP then you're probably using an old processor and you may run into some trouble. Just to be clear xvmc will only work with mpeg2 and not some of the other formats !

thanks for you reply i have already ordered everything i got a p4 2.8 ht sff box and a 5200 low profile nvidia i did not know that i could only playback mpeg2 with xvmc since most of my recordings are in nuv format this will be a problem however most are SD and any HD recordings i make i usually transcode to 1024 768 to save on space so im pretty sure this box will take it im still waiting on some parts to arrive i will definatly post back here to let people know how it all goes

---

### Post by oobe-feisty on 2008-10-06
UPDATE: i finished this project and it work's perfectly 

below are the specs, prices and things to do from my notes


pc $97 hp d530 2.8 ghz 512 ram 40g hdd small tiny form factor known for blowing PSU's new ones cost $35  
graphics $33 USD = low profile agp 5200 nvidia chose this cause 5000 series even though are older can be used with xvmc and color osd ( not that would mean much )
rock vista remote $46
dvi to hdmi cable 15$ 
speakers $35 
cheap tv tuner $42 pinnacle 310i

total = $280 after postage and paypal this is the real total 


stuff to do 

test computer done cdrom doesnt get detected frequently disconnected after install to avoid bios errors

install hardware done needed to saw of parts of the nvidia bracket

test hardware done

install mythbuntu done mythbuntu cd ****** out 3 times during install had to install kubuntu then install mythbuntu desktop then remove kde

setup remote ssh x session or vnc installed and tested vnc havent tested ssh x sesion but ordinary ssh is working and all i really need to use

configure lirc need to do half done

configure mythtv as slave backend decided not to as live tv streams ok 

make sure mythvideo shares can be found done via nfs shares had some trouble with this

install mythvideo mythmusic and other various plugins not time consuming but still havent done it

setup acpi mythwelcome decided not to as mythfrontend has an option to shutdown pc 

make xorg.conf still using default will tweak it later

probably fix overscan still havent plugged it in to tv 

add this line to crontab sudo apt-get -y  --force-yes upgrade



i had plenty of problems along the way but i got it sorted out eventually mostly hardware stuff as most of the part's were second hand i ended up unplugging the dvdrom as it was only detected half the time at boot and the bios wanted me to press f1 to save changes 
this kind of add's to the silence of the machine so i decided to remove the floppy for good measure if anyone is interested i could document this fully but im under the impression there is enough info out there i just couldnt find it at the one place

---

