---
title: "Nvidia driver problems"
date: 2010-11-05
forum: Multimedia Software
---

### Post by wabbit46 on 2010-11-05
I have recently upgraded to Ubuntu 10.10. However the bottom of the screen is cut off with only a trace of it visible.

I had similar problems with version 10.04 where both and top and bottom of the screen were not displayed.  

I have noticed that version 10.10 does not use the proprietry driver the previous versions used.

In desparation I have tried Kubuntu but the results are still much the same.

Does anyone have any idea how I can display a full screen with an Nvidia integrated graphics controller.

---

### Post by sikander3786 on 2010-11-05
Which graphics card is it exactly?

```
lspci | grep VGA
```

Did you install the drivers on 10.10? Which version? Current one?

---

### Post by wabbit46 on 2010-11-08
> **sikander3786 said:**
> Which graphics card is it exactly?

```
lspci | grep VGA
```

Did you install the drivers on 10.10? Which version? Current one?

The command lspci | grep VGA displays nothing. However lspci has an entry for nVidia Corporation NV18 [GeForce 4 HX nForce GPU]

I did a clean Install of Ubuntu 10.10 using the default drivers.

---

### Post by wojox on 2010-11-08
Open a terminal

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

and try configuring the resolution.

---

### Post by wabbit46 on 2010-11-09
> **wojox said:**
> Open a terminal

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

and try configuring the resolution.

The command "sudo nvidia-xconfig" results in the error message "command not found".

Typing gksudo nvidia-settings results in no output

---

### Post by SeijiSensei on 2010-11-09
> **wabbit46 said:**
> I did a clean Install of Ubuntu 10.10 using the default drivers.

Install the proprietary driver using the "Additional Drivers" application.

---

### Post by wabbit46 on 2010-11-10
> **SeijiSensei said:**
> Install the proprietary driver using the "Additional Drivers" application.

This application shows no proprietary in use and I have none available for installtion.

---

### Post by sikander3786 on 2010-11-10
```
lspci | grep VGA
```

This should show your graphics card. If it is not, please post the complete output from

```
lspci
```

> This application shows no proprietary in use and I have none available for installtion.

If it is Nvidia, drivers should be available from Additional Drivers. Are you able to install anything from the repositories actually? Did you successfully install any other software? Is the repository information updated and make sure "Restricted" repository is enabled under Software Center > Edit > Software Sources as that is the one that contains nvidia-current package.

---

### Post by cascade9 on 2010-11-10
GeForce 4MX use the 96.xx drivers. Last I checked, they dont run on 10.10, but that might have changed (I doubt it, or else you should have a driver avaible) 

@ sikander3786- nvidia-current is GF6XXX and higher. It work work with GF4 cards, and trying to make it work could just make things worse.

---

### Post by wabbit46 on 2010-11-10
> **sikander3786 said:**
> ```
lspci | grep VGA
```

This should show your graphics card. If it is not, please post the complete output from

```
lspci
```



If it is Nvidia, drivers should be available from Additional Drivers. Are you able to install anything from the repositories actually? Did you successfully install any other software? Is the repository information updated and make sure "Restricted" repository is enabled under Software Center > Edit > Software Sources as that is the one that contains nvidia-current package.

The command you requested now works since I have re-installed the Operating System.

The output is as below :-
lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by sikander3786 on 2010-11-10
> **wabbit46 said:**
> The command you requested now works since I have re-installed the Operating System.

The output is as below :-
lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
Do the drivers pop up in Additional Drivers now?

As **cascade9** suggested above, I think drivers are no longer available for GeForce 4 MX series in Maverick.

Please take a look here.

[http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)

---

### Post by wabbit46 on 2010-11-11
> **sikander3786 said:**
> Do the drivers pop up in Additional Drivers now?

As **cascade9** suggested above, I think drivers are no longer available for GeForce 4 MX series in Maverick.

Please take a look here.

[http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)
The additional drivers are still not available after the re-install.

I have checked your other reference posting. It looks like Ubuntu 10.10 cannot be made to work correctly on this computer.

Thank you all for your help and advice

---

### Post by cascade9 on 2010-11-12
There is some PPA that is meant to let you install the 96.xx drivers with ubuntu 10.10. I dont know where it is though. :( 

I find it odd that canonical hasnt put the 96.xx drivers into the repos if they work.

---

### Post by sikander3786 on 2010-11-12
96.xx can be installed from Lucid repos in Maverick. The OP in the following thread got it working. Post # 7

[http://ubuntuforums.org/showthread.php?t=1598591](http://ubuntuforums.org/showthread.php?t=1598591)

---

### Post by wabbit46 on 2010-11-15
> **sikander3786 said:**
> 96.xx can be installed from Lucid repos in Maverick. The OP in the following thread got it working. Post # 7

[http://ubuntuforums.org/showthread.php?t=1598591](http://ubuntuforums.org/showthread.php?t=1598591)

I have got a partial fix using Synaptic and searching for nvidia. I installed the package nvidia-96-dev and while it lacks some functionality it at least allows me to view the entire screen

I will not be in a hurry to install future updates of ubuntu.

Thank you all for your assistance

---

