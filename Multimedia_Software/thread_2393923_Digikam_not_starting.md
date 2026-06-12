---
title: "Digikam not starting"
date: 2018-06-10
forum: Multimedia Software
---

### Post by hunterwolf on 2018-06-10
Digikam doesnt' start. Nothing happens clicking the icon.
If I run "digikam" from the terminal I get:

```
digikam: symbol lookup error: /home/hunterwolf/anaconda3/lib/./libharfbuzz.so.0: undefined symbol: FT_Get_Var_Blend_Coordinates
```

---

### Post by gordintoronto on 2018-06-10
What version of Linux do you use? How did you install Digikam?

---

### Post by hunterwolf on 2018-06-11
I'm with Ubuntu 16.04, I installed Digikam via [COLOR=#9E9E9E][FONT=Oxygen]apt-get install digikam[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2018-06-11
The symptoms may show with digikam, but the problem is with whatever program put a couple of libraries in '~/anaconda3/lib/' and configured the system to look there first when searching for libraries. The libs in that directory are different versions from the ones in the repositories and a program expecting the standard versions of the libraries will find them unusable and abort.

Check whether the environment contains a variable 'LD_LIBRARY_PATH' ('echo $LD_LIBRARY_PATH') with a value containing that directory. If it's in there, try unsetting that variable ('unset LD_LIBRARY_PATH') and starting digikam from the shell. If that works, check the startup files of the shell for a line defining the variable and delete it or comment it out.

If there's no LD_LIBRARY_PATH (or unsetting it didn't help) , check '/etc/ld.so.conf' and the files in '/etc/ld.so.conf.d'. If there's a line giving that directory as a source for libraries, use an editor and put a '#' at the beginning of that line. Regenerate the library loader cache with 'sudo ldconfig'.

If neither of these work, then I don't know what that program did to make it's libraries load first and you'll have to wait for someone more knowledgeable to take an interest in this problem.

Holger

---

### Post by hunterwolf on 2018-06-11
thank you so much for your help!

with echo $LD_LIBRARY_PATH I get:
```
/usr/local/cuda-9.0/lib64:/usr/local/cuda/extras/CUPTI/lib64
```

I don't have any "[COLOR=#000000]ld.so.conf" folder.

In "[/COLOR][COLOR=#000000]ld.so.conf.d" folder I edited the file named "cuda-9-0.conf" like so:
#[/COLOR]/usr/local/cuda-9.0/targets/x86_64-linux/lib

then "sudo ldconfig" and "digikam", but nothing changed. same error:
```
digikam: symbol lookup error: /home/hunterwolf/anaconda3/lib/./libharfbuzz.so.0: undefined symbol: FT_Get_Var_Blend_Coordinates
```

Am I missing something?

---

### Post by Holger_Gehrke on 2018-06-11
1) '/etc/ld.so.conf is not a directory, it's a file (which normally just contains an "include" directive to load all the files in /etc/ld.so.conf.d)
2) the line of configuration you commented out is for CUDA (a way to use the GPU for calculations) and completely unrelated to your problem. Better remove the '#' again, otherwise programs using CUDA will fail.

I don't know what this 'anaconda3' in your error message means. I assume it's some kind of program you installed locally into your home directory. You could rename the 'lib' directory in '~/anaconda3' to something else, then digikam should find libharfbuzz in it's standard place. Obviously this will break the application that put them there, so you'll want to rename the directory back to 'lib' before using that program.

Holger

---

### Post by beginner1 on 2018-08-03
Could be a new thread but I upgraded to 18.04.1 and I can't install Digikam due to a dependency issue..
Ideas?
 digikam : Depends: digikam-private-libs (= 4:5.6.0-0ubuntu10) but it is not going to be installed

---

### Post by wildmanne39 on 2018-08-03
Hello beginner1, please start your own thread if you need help with an issue.

Thanks

---

