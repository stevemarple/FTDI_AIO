PDFLATEX = pdflatex
BIBTEX = bibtex
MAKEABBREV = ./makeabbrev

CP = cp -a
.PHONY : doc
doc : images makeabbrev gitlog.tex
	$(PDFLATEX) manual
	$(MAKEABBREV) manual
	$(PDFLATEX) manual

.PHONY : clean
clean:
# .tpt: PDF thumbnails from thumbpdf
	$(RM) -- *.atfi *.aux *.bbl *.blg *.dvi *.lof *.log *.lot *.tpt *.toc */*.aux manual.out manual.upa manual.abb manual.abr _region_.tex


.PHONY : images
images : images/FTDI_AIO_sch.pdf

images/FTDI_AIO_sch.pdf : ../../hardware/v1/FTDI_AIO_sch.pdf
	$(CP) $< $@


makeabbrev : makeabbrev.c

.PHONY : gitlog.tex
gitlog.tex :
	git log -1 --date=iso --format='\newcommand{\gitCommitDate}{%cd}%n\newcommand{\gitCommit}{%H}' . > $@
	git log -1 --date=iso --format='\newcommand{\gitCommitYear}{%cd}' . | sed 's/-[^}]*//' >> $@

