include ../Makefile.defs

TARGET=cilium

all: $(TARGET)

run:
	./cilium

clean:
	go clean
	rm -f $(TARGET)

SOURCES := $(shell find monitor/ policy/ endpoint/ ../daemon ../common . -name '*.go')

$(TARGET): $(SOURCES)
	go build -ldflags "-X "github.com/cilium/cilium/common".Version=$(VERSION)" -o $(TARGET) ./main.go

install: all
	$(INSTALL) -m 0755 $(TARGET) $(DESTDIR)$(BINDIR)
	cp ../contrib/autocomplete/bash_autocomplete /etc/bash_completion.d/cilium
	chmod 644 /etc/bash_completion.d/cilium
	cp $(TARGET) ${GOPATH}/bin
