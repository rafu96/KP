SRC = src
INC = include
OBJ = obj
BIN = bin

CXX = g++
CXXFLAGS = -pedantic -std=c++03 -g -I$(INC) #-O2# -Wall -Wextra

all: $(BIN)/blind_search

# ************ Compilación de módulos ************
$(OBJ)/path.o : $(SRC)/path.cpp $(INC)/path.h
			$(CXX) -c $(CXXFLAGS) $(SRC)/path.cpp -o $(OBJ)/path.o
$(OBJ)/environment.o : $(SRC)/environment.cpp $(INC)/environment.h $(INC)/path.h
			$(CXX) -c $(CXXFLAGS) $(SRC)/environment.cpp -o $(OBJ)/environment.o
$(OBJ)/pathComparison.o : $(SRC)/pathComparison.cpp $(INC)/pathComparison.h $(INC)/environment.h $(INC)/path.h
			$(CXX) -c $(CXXFLAGS) $(SRC)/pathComparison.cpp -o $(OBJ)/pathComparison.o
$(OBJ)/blind_search.o : $(SRC)/blind_search.cpp $(INC)/pathComparison.h $(INC)/environment.h $(INC)/path.h
			-mkdir obj 2> /dev/null
			$(CXX) -c $(CXXFLAGS) $(SRC)/blind_search.cpp -o $(OBJ)/blind_search.o
$(BIN)/blind_search : $(OBJ)/blind_search.o $(OBJ)/pathComparison.o $(OBJ)/environment.o $(OBJ)/path.o
			-mkdir bin 2> /dev/null
			$(CXX) -o $(BIN)/blind_search $(OBJ)/blind_search.o $(OBJ)/pathComparison.o $(OBJ)/environment.o $(OBJ)/path.o


# ************ Limpieza ************
.PHONY: clean mrproper
clean:
	-rm -f $(OBJ)/* $(SRC)/*~ $(INC)/*~ ./*~

mrproper: clean
	-rm -f $(BIN)/*
