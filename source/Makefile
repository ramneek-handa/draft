### -*- mode: makefile-gmake -*-

# Note: If building on Mac OS X, and if you use MacPorts, the following ports
# should be installed:
#
#   texlive-latex
#   texlive-plain-extra
#   texlive-latex-recommended
#   texlive-latex-extra
#   texlive-fonts-recommended
#   texlive-fonts-extra
#   texlive-generic-recommended

FIGURES = $(patsubst %.dot,%.jpg,$(wildcard *.dot))

STDPDF = pdflatex std | grep -v "^Overfull"
STDHTML = htlatex
default: rebuild

images: $(FIGURES)	
clean:
	rm -f *.aux std.pdf *.idx *.ilg *.ind *.log *.lot *.lof *.tmp *.out 
	
refresh:
	$(STDPDF)
	
rebuild:
	$(STDPDF)
	$(STDPDF)
	$(STDPDF)

full: $(FIGURES) grammar xrefs reindex

%.pdf: %.dot
	dot -o $@ -Tpdf $<

%.jpg: %.dot
	dot -o $@ -Tjpg $<

grammar:
	sh ../tools/makegram

xrefs:
	sh ../tools/makexref

reindex:
	$(STDPDF)
	$(STDPDF)
	$(STDPDF)
	makeindex generalindex
	makeindex libraryindex
	makeindex grammarindex
	makeindex impldefindex
	$(STDPDF)
	$(STDPDF)

### Makefile ends here
