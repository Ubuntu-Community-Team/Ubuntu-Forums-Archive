---
title: "looking for method of automated production"
date: 2008-02-26
forum: Multimedia Production
---

### Post by ccclay on 2008-02-26
As a beginner yet, I am looking for the method of automated production starting from easy and simple to complicated job. I believe this will be a help to computer users. With this automated function, we can simply put a mutliamedia file into a folder then it will automatically process the file to our need, such as converting a fla to mpg, converting a wav to mp3, or, rendering a blend file to a 3D photo. Below is my idea using ubuntu to accomplish a simple conversion job.

1. Schedule with cron job at a specified time such as every 3 minutes
2. automatically run the script convertion.py
3. the script will load an conversion application
4. import a fla file from a folder
5. convert the file from fla to mpg
6. save the mpg file , delete the original fla file.

I have tried and know how to do steps from 1 to 3, but my weakness is I dont know how to do the steps from 4 to 5. Is it possible to do those 3 steps ?  Has anyone done similar job and script ? Would you give me some guide ? What I want is to write the script with python. Thank you very much for your help !!

Hope Creative2 may see this ~~
( an idea : I just read the post by Creative2 and am deeply impressed for his great job --- ConvertIT--- and is it possible to use ConvertIT for above purpose ? )

---

### Post by Creative2 on 2008-02-27
well some precisations, i left convertIT and i started Fuoco tools..

i have put a lots of comments on the code(fuoco), and if you look at that you will see how it is simple add or delete functions(on the code and as well as on function file)...well i have used sed...so it's a bit slow but i think it's easier to understand so easier to modify for everyone..

brus46 has started convertIT2 on python and gtk you should talk with him because he has started what you want do and i know it works , not so fine but it works.

Fuoco and ConvertIT can do that  easly (less time stuff)

for fuoco example  you can use every programs

an example is this :

convert a file , and start k3b ...(or if one want start directly to burn...) with this 

encode into xvid for divx player... ENDLOOP  start k3b with your converted files 
```

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4 -o OUTPUT ENDLOOP k3b --datadvd 'OUTDIR'
```

as you can see it converts your files, then ENDLOOP it start growisofs and burn your dvd (thsi command line is under testing...)
```

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4 -o OUTPUT ENDLOOP growisofs -Z /dev/dvd -R -J 'OUTDIR'
```

---

### Post by ccclay on 2008-02-27
Thx Creative so much :) I have visited your Fuocoweb and watched some videos.

So, right now, I first go to ask brus46. I guess it is fine as I will ask and put my questions into your convertIT posting.

---

