package coverage

import (
	"os"
	"testing"
	"time"
	"reflect"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW
func Test_PeopleLen(t *testing.T) {
	personA := Person{
		"A_firstName",
		"A_lastName",
		time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	personB := Person{
		"B_firstName",
		"B_lastName",
		time.Date(2019, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	tData := []struct{
		People People
		Expected int

	} {
		{People: People{}, 			 		Expected: 0},
		{People: People{personA}, 			Expected: 1},
		{People: People{personA, personB}, 	Expected: 2},
	}
	for _, test := range tData{
		got := test.People.Len()
        if got != test.Expected {
			t.Errorf("Expected: %d, got %d", test.Expected, got)
        }
    }
}

func Test_PeopleLess_byBirthDay(t *testing.T) {
	personA := Person{
		"SameFirstName",
		"SameLastName",
		time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	personB := Person{
		"SameFirstName",
		"SameLastName",
		time.Date(2019, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	tData := []struct{
		People People
		Expected bool

	} {
		{People: People{personA, personA}, 	Expected: false},
		{People: People{personB, personB}, 	Expected: false},
		{People: People{personA, personB}, 	Expected: false},
		{People: People{personB, personA}, 	Expected: true},
	}
	for _, test := range tData{
		got := test.People.Less(0, 1)
        if got != test.Expected {
			t.Errorf("Expected: %t, got %t", test.Expected, got)
        }
    }
}

func Test_PeopleLess_byFirstName(t *testing.T) {
	personA := Person{
		"A_FirstName",
		"SameLastName",
		time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	personB := Person{
		"B_FirstName",
		"SameLastName",
		time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	tData := []struct{
		People People
		Expected bool

	} {
		{People: People{personA, personA}, 	Expected: false},
		{People: People{personB, personB}, 	Expected: false},
		{People: People{personA, personB}, 	Expected: true},
		{People: People{personB, personA}, 	Expected: false},
	}
	for _, test := range tData{
		got := test.People.Less(0, 1)
        if got != test.Expected {
			t.Errorf("Expected: %t, got %t", test.Expected, got)
        }
    }
}

func Test_PeopleLess_bySecondName(t *testing.T) {
	personA := Person{
		"SameFirstName",
		"A_LastName",
		time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	personB := Person{
		"SameFirstName",
		"B_LastName",
		time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	tData := []struct{
		People People
		Expected bool

	} {
		{People: People{personA, personA}, 	Expected: false},
		{People: People{personB, personB}, 	Expected: false},
		{People: People{personA, personB}, 	Expected: true},
		{People: People{personB, personA}, 	Expected: false},
	}
	for _, test := range tData{
		got := test.People.Less(0, 1)
        if got != test.Expected {
			t.Errorf("Expected: %t, got %t", test.Expected, got)
        }
    }
}


func Test_PeopleSwap(t *testing.T) {
	personA := Person{
		"A_firstName",
		"A_lastName",
		time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	personB := Person{
		"B_firstName",
		"B_lastName",
		time.Date(2019, time.November, 10, 23, 0, 0, 0, time.UTC),
	}
	tData := []struct{
		People People
		Expected People

	} {
		{People: People{personA, personB}, 	Expected: People{personB, personA}},
		{People: People{personB, personA}, 	Expected: People{personA, personB}},
	}
	for _, test := range tData{
		test.People.Swap(0, 1)
        if !reflect.DeepEqual(test.People, test.Expected) {
			t.Errorf("Expected: %v, got %v", test.Expected, test.People)
        }
    }
}


func Test_MatrixNew(t *testing.T) {
	matrixInputA := 
		`1 2
		 4 5 6
		 7 8 9`
	matrixInputB := 
		`1 2 a3
		 4 5 6
		 7 8 9`
	matrixInputC := 
		`1 2 3
		 4 5 6
		 7 8 9`
	matrixInputD := 
		`1 2
		 3 4
		 5 6`
	matrixInputE := 
		`1 2 3 4
		 5 6 7 8`
	tData := []struct{
		Input string
		Expected bool

	} {
		{Input: matrixInputA, Expected: false},
		{Input: matrixInputB, Expected: false},
		{Input: matrixInputC, Expected: true},
		{Input: matrixInputD, Expected: true},
		{Input: matrixInputE, Expected: true},
	}
	for _, test := range tData{
		got, _ := New(test.Input)
        if (got != nil) != test.Expected {
			t.Errorf("Expected: %t, got %t", test.Expected, got == nil)
        }
    }
}

func Test_MatrixRows(t *testing.T) {
	matrixA, _ := New(
		`1 2 3
		 4 5 6
		 7 8 9`)
	matrixB, _ := New(
		`1 2
		 3 4
		 5 6`)
	matrixC, _ := New(
		`1 2 3
		 4 5 6`)
	tData := []struct{
		Input *Matrix
		Expected [][]int

	} {
		{Input: matrixA, Expected: [][]int{{1, 2, 3}, {4, 5, 6}, {7, 8, 9}}},
		{Input: matrixB, Expected: [][]int{{1, 2}, {3, 4}, {5, 6}}},
		{Input: matrixC, Expected: [][]int{{1, 2, 3}, {4, 5, 6}}},
	}
	for _, test := range tData{
		got := test.Input.Rows()
        if !reflect.DeepEqual(got, test.Expected) {
			t.Errorf("Expected: %v, got %v", test.Expected, got)
        }
    }
}

func Test_MatrixCols(t *testing.T) {
	matrixA, _ := New(
		`1 2 3
		 4 5 6
		 7 8 9`)
	matrixB, _ := New(
		`1 2
		 3 4
		 5 6`)
	matrixC, _ := New(
		`1 2 3
		 4 5 6`)
	tData := []struct{
		Input *Matrix
		Expected [][]int

	} {
		{Input: matrixA, Expected: [][]int{{1, 4, 7}, {2, 5, 8}, {3, 6, 9}}},
		{Input: matrixB, Expected: [][]int{{1, 3, 5}, {2, 4, 6}}},
		{Input: matrixC, Expected: [][]int{{1, 4}, {2, 5}, {3, 6}}},
	}
	for _, test := range tData{
		got := test.Input.Cols()
        if !reflect.DeepEqual(got, test.Expected) {
			t.Errorf("Expected: %v, got %v", test.Expected, got)
        }
    }
}

func Test_MatrixSet(t *testing.T) {

	type Input struct{
		Row int
		Col int
		Value int
		
	}

	matrix, _ := New(
		`1 2 3
		 4 5 6
		 7 8 9`)

	tData := []struct{
		Input Input
		Expected bool

	} {
		{Input: Input{0, 0, -1}, Expected: true},
		{Input: Input{2, 2, -1}, Expected: true},
		{Input: Input{-1, 0, -1}, Expected: false},
		{Input: Input{0, -1, -1}, Expected: false},
		{Input: Input{-1, -1, -1}, Expected: false},
	}
	for _, test := range tData{
		got := matrix.Set(test.Input.Row, test.Input.Col, test.Input.Value)

        if got != test.Expected {
			t.Errorf("Expected: %v, got %v", test.Expected, got)
        }

		if got && matrix.Rows()[test.Input.Row][test.Input.Col] != test.Input.Value {
			t.Errorf("Expected: %d, got %d", test.Input.Value, matrix.Rows()[test.Input.Row][test.Input.Col])
		}

    }
}