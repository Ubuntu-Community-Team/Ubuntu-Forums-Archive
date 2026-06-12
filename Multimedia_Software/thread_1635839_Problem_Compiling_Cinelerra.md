---
title: "Problem Compiling Cinelerra"
date: 2010-12-02
forum: Multimedia Software
---

### Post by Pablo RD on 2010-12-02
Hello!

I'm trying to compile Cinelerra according to the [Cinelerra for Grandma]("http://www.g-raffa.eu/Cinelerra/HOWTO/compilation.html") tutorial, but when I type make in terminal I receive this errors:

> /usr/bin/ld: .libs/libmpeg3.o: relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
.libs/libmpeg3.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: ** [libmpeg3hv.la] Erro 1
make[3]: Saindo do diretório `/home/pablo/cinelerra-cv/libmpeg3'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretório `/home/pablo/cinelerra-cv/libmpeg3'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/pablo/cinelerra-cv'
make: ** [all] Erro 2I researched and found discussions on this exact problem but no solution, can anyone help?

Thanks!

(sorry for my english, I'm Brazilian)

**Edit:**

Problem solved, solution in post [#13]("http://ubuntuforums.org/showpost.php?p=10196623&postcount=13")

---

### Post by cotcot on 2010-12-02
Do you really want to compile cinelerra yourself ?
Have you tried the [[COLOR="Red"]Akirad[/COLOR]]("http://akiradproject.net/repository") repository ? (scroll down to the bottom for instructions)

---

### Post by Pablo RD on 2010-12-02
But how should I proceed using the Meerkat Maverick?

---

### Post by cotcot on 2010-12-02
Maybe the package from lucid works on maverick ?

---

### Post by Pablo RD on 2010-12-02
When I type "deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-lucid main" I receive: Command 'deb' not found 

Oo

---

### Post by AKMask on 2010-12-03
deb isnt a program, its a descriptor used in your sources file. I'd still compile it yourself though, it will be some amount faster since its built for your machine and not a lowest common denominator.

---

### Post by qamelian on 2010-12-03
> **AKMask said:**
> deb isnt a program, its a descriptor used in your sources file. I'd still compile it yourself though, it will be some amount faster since its built for your machine and not a lowest common denominator.
Simply compiling an app on your own machine does not make it faster. You will usually only get a speed increase if there are specific optimizations that you can apply for your hardware. Even then you need to know what those optimizations are and how to apply them.

---

### Post by Yellow Pasque on 2010-12-03
Don't use the --without-pic option if you're running 64-bit.

---

### Post by AKMask on 2010-12-03
> **qamelian said:**
> Simply compiling an app on your own machine does not make it faster. You will usually only get a speed increase if there are specific optimizations that you can apply for your hardware. Even then you need to know what those optimizations are and how to apply them.

Compiling for your instruction set instead of a default i386 yields roughly a 15 percent increase (depending on type of application, im imagining video editing makes a lot of processor calls) before any hand tuned optimizations are even brought to bear per an article in Linux User and Developer magazine.

---

### Post by Pablo RD on 2010-12-03
> Don't use the --without-pic option if you're running 64-bit.


Now I saw a note in the tutorial: 

> In the unlikely event of you having a 64-bit system, the configure command must be shortened to:

   ./configure --with-buildinfo=git/recompile 

but the error persists ... = ( 

I tried the following:
> echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-YOURVERSION main |  sudo tee /etc/apt/sources.list.d/akirad.list && wget -q  [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add -  && sudo apt-get updateBut he says he could not install a dependence: 
> 
Os pacotes a seguir têm dependências desencontradas:
 cinelerra : Depende: libcinelerra (= 2.1.1+git20100325) mas não será instalado
E: Pacotes quebrados
Another way to install Cinelerra?

---

### Post by Yellow Pasque on 2010-12-03
> **Temüjin said:**
> Don't use the --without-pic option if you're running 64-bit.

Did you try this?

---

### Post by qamelian on 2010-12-03
> **AKMask said:**
> Compiling for your instruction set instead of a default i386 yields roughly a 15 percent increase (depending on type of application, im imagining video editing makes a lot of processor calls) before any hand tuned optimizations are even brought to bear per an article in Linux User and Developer magazine.
No, it doesn't. Tests have shown that on modern hardware any speed increase is almost unnoticeable if it exists at all. For some applications, compiling for i686 instead of i386 has actually demonstrated a *decrease* in performance. There is no hard and fast rule. You need to know specifically what optimizations are best for your entire mix of hardware, not just your instruction set. You also need to be aware that some of these optimizations will increase performance, but decrease stability. I've seen this in practice many times over the past 13 years.

---

### Post by mc4man on 2010-12-03
> /usr/bin/ld: .libs/libmpeg3.o: relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
.libs/libmpeg3.o: could not read symbols: Bad value
That's a very specific error, it's trying to link against a non pic libmpeg3.
Your source uses an internal version so I'd suggest you need to clean your source completely before attempting a new configure (as Temüjin suggested),  and build.

So cd to source folder and run this, then configure and build and you'll be fine.
```
make distclean
```

Or if wanting a ppa see this thread post 6
[http://ubuntuforums.org/showthread.php?p=10189570#post10189570](http://ubuntuforums.org/showthread.php?p=10189570#post10189570)

---

### Post by Pablo RD on 2010-12-05
> **Temüjin said:**
> Did you try this?

Sorry, I had quoted the wrong post. I tried to do.
  
> **mc4man said:**
> That's a very specific error, it's trying to link against a non pic libmpeg3.
Your source uses an internal version so I'd suggest you need to clean your source completely before attempting a new configure (as Temüjin suggested),  and build.

So cd to source folder and run this, then configure and build and you'll be fine.
```
make distclean
```Or if wanting a ppa see this thread post 6
[http://ubuntuforums.org/showthread.php?p=10189570#post10189570](http://ubuntuforums.org/showthread.php?p=10189570#post10189570)

Ohh yeah, it was exactly that! I installed cinelerra.

Thanks!

(solved)

---

