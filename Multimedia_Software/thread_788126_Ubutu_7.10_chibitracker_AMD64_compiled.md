---
title: "Ubutu 7.10 chibitracker AMD64 compiled"
date: 2008-05-09
forum: Multimedia Software
---

### Post by hipohondorm on 2008-05-09
Hello, I successfully compiled chibitracker under AMD64 UbuntuStudio 7.10.
I'm a complete rookie but it was some achievement for me, that's why I'd like to share my experiences :)
The problem for me was g++ constantly crashing with $int64 and Uint64 data type declaration collision. 

- download necessary g++ compiler packages + 
- download latest chibitracker sources from chibitracker.berios.de
   (my version was 1.2)
- sudo apt-get install libsdl1.2-dev (latest SDL dev package - chibitracker dependance)
- sudo apt-get scons (installer used for chibitracker)
- untar chibitracker sources
- issue 'scons' command in chibitracker source directory
If the compiler exits without errors, you are lucky. Issue 'sudo scons install' command and you're done.

If the compiler gives errors about $int64 and Uint64 declaration collision:
- save backup copy of /usr/include/SDL/SDL_stdinc.h
- edit /usr/include/SDL/SDL_stdinc.h and replace the code:

#ifdef SDL_HAS_64BIT_TYPE
/*typedef int64_t		Sint64;*/
/*typedef uint64_t	Uint64;*/
#else
/* This is really just a hack to prevent the compiler from complaining */
typedef struct {
	Uint32 hi;
	Uint32 lo;
} Uint64, Sint64;
#endif

with:

typedef signed long long Sint64;
typedef unsigned long long Uint64;

- Now issue 'scons' again in chibitracker source directory.
- If successful, issue 'sudo scons install' and you're done.

I know that it's not elegant to mess with SDL headers, but I was desperate to run chibi on my PC. It works, although it coredumps every time application exits. But I don't care, all my data is correctly saved.

---

