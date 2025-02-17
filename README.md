#HTS Engine Python Extension

[![Build Status](https://travis-ci.org/sih4sing5hong5/hts_engine_python.svg?branch=master)](https://travis-ci.org/sih4sing5hong5/hts_engine_python)

This package is an extension for whose want to use hts engine by Python 3.

htsengine will update when hts_engine updating.

## Installation
```bash
pip install htsengine
```

### Uninstallation
```bash
pip uninstall htsengine
```

## Usage
See `example/example.py`
```python3
import htsengine
model = 'Taiwanese.htsvoice'
label = [line.rstrip() for line in open('full.lab')]

s, f, n, a = htsengine.synthesize(model, label)
import wave
wavFile = wave.open('result.wav', 'wb')
wavFile.setsampwidth(s)
wavFile.setframerate(f)
wavFile.setnchannels(n)
wavFile.writeframesraw(a)
wavFile.close()
```

## Update with newest hts_engine
```bash
sudo apt-get install -y git-cvs 
rsync -av --delete rsync://hts-engine.cvs.sourceforge.net/cvsroot/hts-engine/ csv_data
git checkout origin
git cvsimport -p x -v -d `pwd`/csv_data/ hts_engine_API
git checkout master
git push origin origin
```
refer:http://ghantoos.org/2010/11/11/migrating-sourceforge-cvs-source-repository-to-github/

If I forget to update, please contact me by pull request on github.

Github website: https://github.com/sih4sing5hong5/hts_engine_python

## Install HTS Engine Execution Files
1. Enter the src/ directory.
2. Run this two commands:
```bash
	aclocal
	autoconf
```
3. Generate the ChangeLog file, you choice one command to run:
```bash
	git log > ChangeLog # if you have the git version control
	cvs log > ChangeLog # if you have the cvs version control
	touch ChangeLog # otherwise
```
4. Run this command:
```bash
	automake --add-missing
```
5. And then see the src/INSTALL file.

##HTS Engine Readme
```
===============================================================================
      The HMM-Based Speech Synthesis Engine "hts_engine API" version 1.08
                           release December 25, 2013


The hts_engine API is an API version of hts_engine which has been released
since HTS version 1.1. It has been being developed by the HTS working group
(see "Who we are" below) and some graduate students in Nagoya Institute of
Technology (see "AUTHORS" in the same directory).

*******************************************************************************
                                    Copying
*******************************************************************************

The hts_engine API is released under the Modified BSD license (see
http://www.opensource.org/). Using and distributing this software is free
(without restriction including without limitation the rights to use, copy,
modify, merge, publish, distribute, sublicense, and/or sell copies of this
work, and to permit persons to whom this work is furnished to do so) subject to
the conditions in the following license:

/* ----------------------------------------------------------------- */
/*           The HMM-Based Speech Synthesis Engine "hts_engine API"  */
/*           developed by HTS Working Group                          */
/*           http://hts-engine.sourceforge.net/                      */
/* ----------------------------------------------------------------- */
/*                                                                   */
/*  Copyright (c) 2001-2013  Nagoya Institute of Technology          */
/*                           Department of Computer Science          */
/*                                                                   */
/*                2001-2008  Tokyo Institute of Technology           */
/*                           Interdisciplinary Graduate School of    */
/*                           Science and Engineering                 */
/*                                                                   */
/* All rights reserved.                                              */
/*                                                                   */
/* Redistribution and use in source and binary forms, with or        */
/* without modification, are permitted provided that the following   */
/* conditions are met:                                               */
/*                                                                   */
/* - Redistributions of source code must retain the above copyright  */
/*   notice, this list of conditions and the following disclaimer.   */
/* - Redistributions in binary form must reproduce the above         */
/*   copyright notice, this list of conditions and the following     */
/*   disclaimer in the documentation and/or other materials provided */
/*   with the distribution.                                          */
/* - Neither the name of the HTS working group nor the names of its  */
/*   contributors may be used to endorse or promote products derived */
/*   from this software without specific prior written permission.   */
/*                                                                   */
/* THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND            */
/* CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES,       */
/* INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF          */
/* MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE          */
/* DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS */
/* BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,          */
/* EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED   */
/* TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,     */
/* DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON */
/* ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,   */
/* OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY    */
/* OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE           */
/* POSSIBILITY OF SUCH DAMAGE.                                       */
/* ----------------------------------------------------------------- */

Although this software is free, we still offer no warranties and no
maintenance. We will continue to endeavor to fix bugs and answer queries when
can, but are not in a position to guarantee it. We will consider consultancy if
desired, please contacts us for details.

If you are using the hts_engine API in commercial environments, even though no
license is required, we would be grateful if you let us know as it helps
justify ourselves to our various sponsors. We also strongly encourage you to

 * refer to the use of hts_engine API in any publications that use this
   software
 * report bugs, where possible with bug fixes, that are found

See also "COPYING" file in the current directory for details.

*******************************************************************************
                                 Installation
*******************************************************************************

See "INSTALL" in the same directory for details.

*******************************************************************************
                                 Documentation
*******************************************************************************

Reference manual of hts_engine API is available at

http://hts-engine.sourceforge.net/

*******************************************************************************
                               Acknowledgements
*******************************************************************************

Keiichi Tokuda
Shinji Sako
Heiga Zen
Keiichiro Oura
Kazuhiro Nakamura
Keijiro Saino

*******************************************************************************
                                  Who we are
*******************************************************************************

The HTS working group is a voluntary group for developing the HMM-Based Speech
Synthesis System. Current members are

 Keiichi Tokuda      http://www.sp.nitech.ac.jp/~tokuda/
 (Produce and Design)
 Keiichiro Oura      http://www.sp.nitech.ac.jp/~uratec/
 (Design and Development, Main Maintainer)
 Kei Hashimoto       http://www.sp.nitech.ac.jp/~bonanza/
 Sayaka Shiota       http://www.sp.nitech.ac.jp/~sayaka/
 Shinji Takaki       http://www.sp.nitech.ac.jp/~k-prr44/
 Heiga Zen
 Junichi Yamagishi   http://homepages.inf.ed.ac.uk/jyamagis/
 Tomoki Toda         http://spalab.naist.jp/~tomoki/index_e.html
 Takashi Nose
 Shinji Sako         http://www.mmsp.nitech.ac.jp/~sako/
 Alan W. Black       http://www.cs.cmu.edu/~awb/

and the members are dynamically changing. The current formal contact address of
HTS working group and a mailing list for HTS users can be found at
http://hts.sp.nitech.ac.jp/
===============================================================================
```
