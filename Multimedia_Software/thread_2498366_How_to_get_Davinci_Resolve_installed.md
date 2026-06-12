---
title: "How to get Davinci Resolve installed?"
date: 2024-06-10
forum: Multimedia Software
---

### Post by morcar1975 on 2024-06-10
I have used DR on many systems and I just switched to the latest Ubuntu.

My system has the Ryzen 9 7950X and the Radeon 7900XTX.

I downloaded the zip file and ran it, but it says I am missing files.

> Please install the following missing packages:
    libapr1 libaprutil1 libasound2 libglib2.0-0


So I went to install the files through the terminal and I got this message

> sudo apt install libapr1 libaprutil1 libasound2 libglib2.0-0
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'libapr1t64' instead of 'libapr1'
Note, selecting 'libaprutil1t64' instead of 'libaprutil1'
Note, selecting 'libglib2.0-0t64' instead of 'libglib2.0-0'
Package libasound2 is a virtual package provided by:
  liboss4-salsa-asound2 4.2-build2020-1ubuntu3
  libasound2t64 1.2.11-1build2 (= 1.2.11-1build2)
You should explicitly select one to install.


E: Package 'libasound2' has no installation candidate


Can anyone help me in getting DR to install, please.

Thanks

---

### Post by Yellow Pasque on 2024-06-11
```
sudo apt install libapr1t64 libaprutil1t64 libasound2t64 libglib2.0-0t64
```

---

### Post by morcar1975 on 2024-06-11
Those are already installed, but I still get the errors

---

### Post by Yellow Pasque on 2024-06-12
Then either it really wants the corresponding -dev packages or something is wrong with the installer.
```
sudo apt install libapr1-dev libaprutil1-dev libasound2-dev libglib2.0-dev
```
If it still doesn't work, then you should probably ask on the DR forum, or give a link to the specific .zip you are talking about (assuming it's free) so we can investigate more.

---

### Post by easydawg on 2024-07-08
[SIZE=3][FONT=arial]I'm going to move from Mint to [COLOR=#000000]**Ubuntu 22.04.4 HWE** which is what my **AMD GPU** Drivers will be looking for.

Saw a YouTube video showing a massive amount of work through the terminal to get DR working on **Ubuntu 24.04** but mentioned DR runs on 22.04.

I see this in the post: [/COLOR]
[/FONT][/SIZE][SIZE=3][FONT=arial]sudo apt install libapr1-dev libaprutil1-dev libasound2-dev libglib2.0-dev


Is this a list of dependencies that need to be loaded via the terminal prior to installing DR via the .run file? 

I'm running **DR 19.3 Studio**

In Mint I had 4 or 5 dependencies like that.
[/FONT][/SIZE][SIZE=3][FONT=arial][B][COLOR=#000000]

[/COLOR][/B][/FONT][/SIZE]

---

### Post by Yellow Pasque on 2024-07-08
> **easydawg said:**
> I'm going to move from Mint to [COLOR=#000000]**Ubuntu 22.04.4 HWE** which is what my **AMD GPU** Drivers will be looking for.

Mint (21) is based on Ubuntu 22.04, uses the same kernel, etc. So I don't see a point to that.

---

### Post by easydawg on 2024-07-08
Okay so you triggered me to research some more and it looks like I will stay with Mint! 

Sounds like Mint 22 is on the way with some nice updates.

From what I saw Ubuntu has undesirable tendencies coming from management. Didn't read too much into it. 

My main thing was having a system that my new GPU, entire new machine build, will be compatible with.

Then my only hurdle is keeping Davinci Resolve running which I do fairly well with right here on Mint.

---

### Post by easydawg on 2024-07-08
Still struggling? 

**Are you running 24.04?**

Here's the AMD Driver specs: Radeon&#8482; Software for Linux® version 24.10.3 for [COLOR=#ff0000]**Ubuntu 20.04.6 HWE**[/COLOR]

I did see a video showing all the hoops to jump through to get Davinci running on 24.04 but then heard 1 short sentence saying **[COLOR=#ff0000]DR will work with 22.04.[/COLOR]** 

That was all I needed to hear.

I also got enlightened when saying I was going to Ubuntu 22.04 from Mint and was told Mint runs on the same 22.04 so I can just stay with Mint.

These are the dependencies I installed to get DR19.3 Studio running on Mint Cinnamon 21.3:

[B][COLOR=#0000cd]sudo apt install [/COLOR][COLOR=#000000]libapr1 libaprutil1 libxcb-composite0 libxcb-cursor0 libxcb-damage0

[/COLOR][/B][COLOR=#000000]PS: I did have GPU issues updating to DR 19.4 so had to go back to 19.3[/COLOR]**[COLOR=#000000][/COLOR][COLOR=#0000cd][/COLOR]**

---

### Post by afrodeity on 2024-08-29
This worked for me on Ubuntu 22.04


```

cd /opt/resolve/libs
sudo mkdir not_used
sudo mv libgio* not_used
sudo mv libgmodule* not_used
```

Of course, you will need a GPU.

---

### Post by loganwilson33 on 2024-09-10
This worked for me on Ubuntu 22.04 as well

---

### Post by JD82 on 2024-10-22
> **easydawg said:**
> [SIZE=3][FONT=arial]I'm going to move from Mint to [COLOR=#000000]**Ubuntu 22.04.4 HWE** which is what my **AMD GPU** Drivers will be looking for.

Saw a YouTube video showing a massive amount of work through the terminal to get DR working on **Ubuntu 24.04** but mentioned DR runs on 22.04.
[/COLOR][/FONT][/SIZE]

Hi there,

I realize this is coming months after the OP, but if you're still trying to get DaVinci Resolve working on Ubuntu 24.04, I have a solution that might help. I wrote an Ansible script that automates the entire process, so there's no need for the massive amount of manual work through the terminal that you've seen in other guides.

This script handles downloading the official installer, setting up symlinks to avoid downgrading dependencies, and detecting whether you're using an AMD, Intel, or Nvidia GPU to install the correct OpenCL libraries. It also sets up the necessary udev rules for USB peripherals like DaVinci Panels and installs all system icons and MIME files, so everything is properly integrated.

Here&#8217;s how you can use the script:

1. Install Git and Make if they aren&#8217;t already installed:
    ```

    sudo apt install git make
    
```

2. Clone the repository:
    ```

    git clone https://github.com/leinardi/JDInstaller.git
    
```

3. Switch to the repository directory:
    ```

    cd JDInstaller
    
```

4. Check out the DaVinci Resolve branch (it&#8217;s disabled by default in the main script):
    ```

    git checkout davinci
    
```

5. Run the installation:
    ```

    make install TAGS=davinci_resolve
    
```

The script should make the process much easier, fully automating what would normally be a lot of manual steps. You can check out the full script and details here: [https://github.com/leinardi/JDInstaller](https://github.com/leinardi/JDInstaller)

---

### Post by pczekalski on 2024-10-22
Just installed 19.0.3 on a fresh 24.04.01 Ubuntu with the help of the following guide:
[https://www.reddit.com/r/davinciresolve/comments/1eaepzh/how_to_upgradeinstall_davinci_resolve_190b5_free/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button](https://www.reddit.com/r/davinciresolve/comments/1eaepzh/how_to_upgradeinstall_davinci_resolve_190b5_free/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
Works like a charm even on integrated Intel + eGPU (NVIDIA 2080Ti in RazorX Thunderbolt enclosure).

---

### Post by asherax on 2024-10-23
did you read? [https://www.reddit.com/r/davinciresolve/comments/1eaepzh/how_to_upgradeinstall_davinci_resolve_190b5_free/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button&rdt=36039](https://www.reddit.com/r/davinciresolve/comments/1eaepzh/how_to_upgradeinstall_davinci_resolve_190b5_free/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button&rdt=36039)

---

