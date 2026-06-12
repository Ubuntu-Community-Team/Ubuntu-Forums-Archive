---
title: "Final Cut on LINUX?"
date: 2007-05-22
forum: Multimedia Production
---

### Post by cgbier on 2007-05-22
Still looking for an NLE on Ubuntu. The offerings at the moment are nothing to write home about.

Tried to install my Sony Vegas under WINE, but no go. Now I thought if it would be possible to get the Intel-Mac version of Final Cut to run on Ubuntu.
Would there be a way?

---

### Post by jkwarras on 2007-05-23
I'll also love to know if this is possible and how ;)

---

### Post by NumberOne on 2007-05-23
I know there is a version of final cut for OSX.  I don't know if it will run on Ubuntu.

---

### Post by drosky on 2007-05-23
> **NumberOne said:**
> I know there is a version of final cut for OSX.  I don't know if it will run on Ubuntu.

This probably isn't a great approach.  It won't run in Wine,  so the only chance for it to work would be to run OS X in VMWare, but this, while possible, is pretty tricky and has lots of limitations.  If one of the native Linux choices is not adequate, you would probably have better luck using a windows-based NLE in VMWare (if it won't run properly in Wine).

---

### Post by cgbier on 2007-05-23
I was trying to install my Sony Vegas in WINE, but didn't get it to work. As I'm using Final Cut on the job, it would be fun to have it at home also .... especially as I tend to mix up shortcuts between F/C and Vegas.

Problem is I can afford either the software OR the Mac at the moment, but not both :(

---

### Post by drosky on 2007-05-23
> **cgbier said:**
> I was trying to install my Sony Vegas in WINE, but didn't get it to work. As I'm using Final Cut on the job, it would be fun to have it at home also .... especially as I tend to mix up shortcuts between F/C and Vegas.

Problem is I can afford either the software OR the Mac at the moment, but not both :(

Wine is always improving, but there's still only a relatively small number of apps that Wine runs really well.  There's a pretty god change, however, that Vegas will run in VMWare.  If you wnat to try this, don't install vmware-player from the Ubuntu repositories.  Download VMWare Workstation from vmware.com.  It comes with the player, and you'll need the Workstation part to create the VM in the first place.

---

### Post by cgbier on 2007-05-23
The sad thing is that older versions of Vegas (before it was bought by Sony) worked under WINE.

I tried VMware, but in combination with Vegas it took too many resources from the machine. It was running like molasses.

---

### Post by drosky on 2007-05-24
> **cgbier said:**
> The sad thing is that older versions of Vegas (before it was bought by Sony) worked under WINE.

I tried VMware, but in combination with Vegas it took too many resources from the machine. It was running like molasses.

Are you giving the VM plenty of memory?  I've seen cases where people had 1Gig of RAM on their machine, but were only giving the VM as little as 128Meg.  Something like that could cause issues with an XP client running a large application.

---

### Post by cgbier on 2007-05-24
Thanks for the hint. No, I had given it 512 Meg .... the rest of my 1.25 gig went to Sony.

Main problem was actually not the editing (which was also slow), but the more processor intensive rendering. In the preview, I couldn't get the frame rate above 5 or 6 fps (despite rendering into RAM), and the final compression and rendering took nearly double the time than under pure XP.

---

### Post by eye208 on 2007-05-25
> **cgbier said:**
> Still looking for an NLE on Ubuntu. The offerings at the moment are nothing to write home about.
Try Blender.

---

### Post by Prisma on 2007-06-01
But blender is and application for 3D modeling, NLEs  are for video editing.

[http://en.wikipedia.org/wiki/Non-linear_editing_system]("http://en.wikipedia.org/wiki/Non-linear_editing_system")

---

### Post by Rexbron! on 2007-06-02
> **Prisma said:**
> But blender is and application for 3D modeling, NLEs  are for video editing.

[http://en.wikipedia.org/wiki/Non-linear_editing_system]("http://en.wikipedia.org/wiki/Non-linear_editing_system")

Yes, but blender has a very powerful compositing engine and can handle video. It does visual effects better than anything else on linux right now AFAIK.

As for just splicing clips together, cinelerra or any other of your choosing will work fine.

Rather than looking for one app to do everything, see if the ones out now can be put together such that the strengths of each are leveraged. 

I am working on a workflow myself for getting 24p footage from the Canon HV20 all the way through post. It is not unified, but currently I can capture and convert the captured footage back to 24 fps. If anyone is interested I will post when I have something more solid.

---

### Post by Prisma on 2007-06-02
> **Rexbron! said:**
> Yes, but blender has a very powerful compositing engine and can handle video. It does visual effects better than anything else on linux right now AFAIK.

As for just splicing clips together, cinelerra or any other of your choosing will work fine.

Rather than looking for one app to do everything, see if the ones out now can be put together such that the strengths of each are leveraged. 

I am working on a workflow myself for getting 24p footage from the Canon HV20 all the way through post. It is not unified, but currently I can capture and convert the captured footage back to 24 fps. If anyone is interested I will post when I have something more solid.

Wow! I am planing to buy the same freaking camera to shot my next project. It is amazing. it captures 24p HD natively. please post more info I am really interested to get native 24p HD on my linux box so I dont have to go back to windows just to use sony vegas for editing my projects.

also what kind of video effects can blender do with your raw footage? would you please explain to me i am really interested.


Thanks   :)

---

### Post by Rexbron! on 2007-06-02
I am still experimenting with blender, but hop on #ubuntustudio and ping a guy named troy_s. He is very knowledgeable (compared to me) and he is the guy I am working with on this project. 

The current issue with blender is that it has trouble with the 24000/1001 frame rate (23.976), but the dev's have been notified and are looking into it. 

As for capturing, get the latest version of dvgrab and get all the hdv patches (from the sf dvgrab page) and compile it. That will get you the interlaced  footage as it exists on tape. 

I have yet to do a sync test for long takes, but my thought is that it will be fine. 

Currently, troy_s and myself are working on fine tuning a script that uses mencoder to convert the footage back to 24p from the 60i it is recorded to on the tape.

---

### Post by carusoswi on 2007-06-03
> **cgbier said:**
> The sad thing is that older versions of Vegas (before it was bought by Sony) worked under WINE.

I tried VMware, but in combination with Vegas it took too many resources from the machine. It was running like molasses.

Which version of Vegas/Vegas Video worked under Wine?  I run Crossover and own all versions of Vegas from 2.0 up.  

Caruso

---

### Post by carusoswi on 2008-03-02
> **carusoswi said:**
> Which version of Vegas/Vegas Video worked under Wine?  I run Crossover and own all versions of Vegas from 2.0 up.  

Caruso

Seems I've come full circle.  Was browsing the Vegas forums and came across a thread showing Vegas 5 up and running on an Ubuntu machine.  So, I tried to install using both Crossover and Wine.  No go.  Complains about Net.1.  I downloaded 'net' but have yet to find the proper way to implement it so that it is recognized by Vegas during the install.

FWIW, I tried to install Vegas 5 and Vegas 2.

Vegas 2 aborts with complaints about needing Directx8.

What to do?

Anyone?

Caruso

---

